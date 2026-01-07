# 📚 Book Explorer App

An Android app built with **XML Layouts and ViewBinding** that lets you explore books using the **Google Books API**.  
This project is designed to practice and demonstrate modern Android development concepts like **MVVM, Clean Architecture, Manual DI, Flows, RoomDB, Paging 3, Navigation Component, and Unit Testing**.

---

## 📸 Screenshots

<table>
  <tr>
    <td><img alt="Home Screen" src="https://github.com/aetrna300bpm/prj-android/blob/main/Books-Home.png" height="300"/></td>
    <td><img alt="Detail Screen" src="https://github.com/aetrna300bpm/prj-android/blob/main/Books-Details.png" height="300"/></td>
    <td><img alt="Search Screen" src="https://github.com/aetrna300bpm/prj-android/blob/main/Books-Search.png" height="300"/></td>
  </tr>
  <tr>
    <td><img alt="Wishlist Screen" src="https://github.com/aetrna300bpm/prj-android/blob/main/Books-Wishlist.png" height="300"/></td>
    <td><img alt="Profile Screen" src="https://github.com/aetrna300bpm/prj-android/blob/main/Books-Profile.png" height="300"/></td>
  </tr>
</table>

---

## ✨ Features
- 🔎 Search books by keywords
- 📖 View detailed book information (title, author, description, cover image)
- ❤️ Save books to favorites list (stored locally with RoomDB)
- 📚 Manage reading list with custom statuses and notes
- 📑 Pagination with infinite scroll using Paging 3
- 👤 Simple profile screen
- 🌐 Open book preview links in browser

---

## 🛠️ Tech Stack
- **UI:** XML Layouts + ViewBinding (Material Design 3)
- **Navigation:** Navigation Component with Fragments
- **Architecture:** MVVM + Clean Architecture
- **Asynchronous:** Kotlin Coroutines, Flow
- **Dependency Injection:** Manual DI (AppContainer pattern)
- **Networking:** Retrofit + OkHttp
- **Local Storage:** Room Database
- **Pagination:** Paging 3
- **Image Loading:** Coil
- **Testing:** JUnit, MockK
- **Static Analysis:** Detekt + Ktlint
- **Build System:** Gradle with Kotlin DSL

---

## 🏗️ Project Structure

```plaintext
com.alpha.books_explorer/ 
│ 
├── data/                           # Data Layer (API + DB) 
│   ├── local/                      # Room database 
│   │   ├── converters/ 
│   │   │   └── Converters.kt 
│   │   ├── dao/ 
│   │   │   ├── FavBookDao.kt 
│   │   │   └── ReadingListDao.kt 
│   │   ├── entities/ 
│   │   │   ├── BookEntity.kt 
│   │   │   └── ReadingListEntity.kt 
│   │   └── BooksDatabase.kt 
│   │ 
│   ├── paging/  
│   │   └── BooksPagingSource.kt 
│   │
│   ├── remote/                     # Retrofit API 
│   │   ├── BookApiService.kt 
│   │   └── dto/ 
│   │       ├── BookSearchResponse.kt 
│   │       └── VolumeInfoDto.kt 
│   │ 
│   ├── repository/                 # Repository implementation 
│   │   └── BookRepositoryImpl.kt 
│   │ 
│   └── mappers/                    # DTO ↔ Entity ↔ Domain 
│       └── BookMapper.kt 
│ 
├── domain/                         # Domain Layer (business logic) 
│   ├── model/ 
│   │   ├── Book.kt 
│   │   ├── VolumeInfo.kt 
│   │   └── ImageLinks.kt 
│   │ 
│   ├── repository/                 # Abstract repository interfaces 
│   │   └── BookRepository.kt 
│   │ 
│   └── usecase/                    # Use cases 
│       ├── GetBooksUseCase.kt 
│       ├── SearchBooksUseCase.kt 
│       ├── GetBookByIdUseCase.kt 
│       ├── FavList/ 
│       │   ├── AddIntoFavListUseCase.kt 
│       │   ├── GetAllFavBooksUseCase.kt 
│       │   ├── IsBookPresentInFavListUseCase.kt 
│       │   └── RemoveFromFavListUseCase.kt 
│       └── readingList/ 
│           ├── AddIntoReadingListUseCase.kt 
│           ├── GetAllReadingListBooksUseCase.kt 
│           ├── GetBookFromReadingListUseCase.kt 
│           ├── IsBookPresentInReadingListUseCase.kt 
│           └── RemoveFromReadingListUseCase.kt 
│ 
├── di/                             # Dependency Injection (Manual DI) 
│   ├── AppContainer.kt             # Interface định nghĩa dependencies
│   └── DefaultAppContainer.kt      # Implementation của AppContainer
│ 
├── presentation/                   # Presentation Layer 
│   ├── ui/                         # UI với Fragments & XML Layouts
│   │   ├── adapter/ 
│   │   │   ├── BookAdapter.kt 
│   │   │   └── BookPagingAdapter.kt 
│   │   ├── home/ 
│   │   │   ├── HomeFragment.kt 
│   │   │   ├── HomeViewModel.kt 
│   │   │   └── HomeUiState.kt 
│   │   ├── search/ 
│   │   │   ├── SearchFragment.kt 
│   │   │   ├── SearchViewModel.kt 
│   │   │   └── SearchUiState.kt 
│   │   ├── details/ 
│   │   │   ├── BookDetailFragment. kt 
│   │   │   ├── BookDetailViewModel. kt 
│   │   │   └── BookDetailUiState.kt 
│   │   ├── wishList/ 
│   │   │   ├── FavListFragment.kt 
│   │   │   ├── FavListViewModel.kt 
│   │   │   ├── ReadingListFragment.kt 
│   │   │   ├── ReadingListViewModel.kt 
│   │   │   └── WishlistUiState.kt 
│   │   └── profile/ 
│   │       ├── ProfileFragment.kt 
│   │       └── ProfileViewModel.kt 
│   │ 
│   └── navigation/ 
│       └── nav_graph.xml           # Navigation graph
│ 
├── MainActivity.kt                 # Host Activity with BottomNavigationView
└── BooksExplorerApplication.kt     # Application class (AppContainer initialization)  

```

---

## 🔌 API Reference
 - **Google Books API** → https://developers.google.com/books/docs/v1/using

    **Example request:** https://www.googleapis.com/books/v1/volumes?q=android

---

## 📚 Learning Purpose
This app was built to cover: 
* XML Layouts + ViewBinding
* Fragment-based Navigation with Navigation Component
* RoomDB for local storage
* Kotlin Coroutines + Flows 
* Manual Dependency Injection (AppContainer pattern)
* MVVM + Clean Architecture
* Retrofit Networking
* Paging 3 for pagination
* Coil for image loading
* Writing Unit Tests with MockK
* Enforcing code quality with Detekt + Ktlint

---

## 🚀 Getting Started

### Prerequisites
- Android Studio Hedgehog or newer
- JDK 11 or higher
- Android SDK with API level 24+

### Installation
1. Clone the repository: 
```bash
git clone https://github.com/aetrna300bpm/prj-android.git
```

2. Open the project in Android Studio

3. Sync Gradle files

4. Run the app on an emulator or physical device

---

## 🧪 Testing
Run unit tests: 
```bash
./gradlew test
```

Run Detekt static analysis:
```bash
./gradlew detekt
```

Run Ktlint code formatting check:
```bash
./gradlew ktlintCheck
```

---

## 👨‍💻 Author
**tranvananhanhanh**
- GitHub: [@tranvananhanhanh](https://github.com/tranvananhanhanh)
- Repository: [aetrna300bpm/prj-android](https://github.com/aetrna300bpm/prj-android)

---

## 📄 License
This project is for educational purposes. 

---

## 🙏 Acknowledgments
- Original concept inspired by various Android development learning resources
- Google Books API for providing the book data
- Android community for excellent documentation and libraries
```