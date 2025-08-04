
# ✂️ URL Shortener Challenge

[![Kotlin](https://img.shields.io/badge/Kotlin-1.9.0-blue.svg)](https://kotlinlang.org/)
[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)

A simple Android application built with Kotlin and Jetpack Compose that allows users to shorten URLs and see a history of their recently shortened links using a REST API provided by .

---

## 📱 Features

- **URL Shortening**: Input a full URL and get a short alias
- **Shortened Link List**: View recent shortened URLs on the same screen
- **Stateless Storage**: Links are kept in memory only
- **API Integration**: Connects to a backend via REST (Heroku)
- **Fallback Mode**: Uses a built-in fake API if the main API is offline
- **Jetpack Compose UI**: Single-screen interface built entirely in Compose
- **Error Handling**: Manages API failure states with fallback logic
- **Unit Testing**: Core logic tested using JUnit and MockK

---

## 🛠️ Tech Stack

- **Language**: [Kotlin](https://kotlinlang.org/)
- **UI**: [Jetpack Compose](https://developer.android.com/jetpack/compose)
- **Architecture**: MVVM + Clean Architecture
- **State Management**: ViewModel + StateFlow
- **Networking**: [Ktor Client](https://ktor.io/)
- **Testing**: JUnit, MockK

---

## 🚀 Getting Started

### Prerequisites

- Android Studio Hedgehog (2023.1.1) or newer
- Android SDK 34
- JDK 17
- Gradle 8.0+

### Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/url-shortener.git
   cd url-shortener
   ```

2. Open the project in Android Studio and run the app on an emulator or device.

---

## 🏗️ Project Structure

```
app/
├── src/
│   ├── main/
│   │   ├── java/com/example/nubankshortener/
│   │   │   ├── data/            # API models and repository
│   │   │   ├── domain/          # Use cases and entities
│   │   │   ├── presentation/    # Compose UI + ViewModel
│   │   │   ├── di/              # Dependency Injection setup
│   │   │   └── utils/           # Fallback/fake API handling
│   │   └── res/                 # UI resources
│   ├── test/                    # Unit tests
│   └── androidTest/            # UI tests (optional)
```

---

## 🧪 Testing

- **Unit Tests**: URL shortening logic, state handling
- **Frameworks**: JUnit, MockK

---

## 🌐 API

Base URL: `https://url-shortener-nu.herokuapp.com`

### 🔹 Shorten URL

- **POST** `/api/alias`
- **Body**: `{ "url": "<your_url>" }`
- **Response**:
  ```json
  {
    "alias": "abc123",
    "_links": {
      "self": "https://original.url",
      "short": "https://sou.nu/abc123"
    }
  }
  ```

### 🔸 Read Shortened URL

- **GET** `/api/alias/{id}`
- **Response**:
  ```json
  { "url": "https://original.url" }
  ```

- `404` if alias not found

---

## 💡 Notes

🛠️ **Offline Fallback**:  
During testing, the provided Heroku API was unavailable (returning 404). As a differentiator, a **fake API** was implemented to simulate the backend and ensure the app remained functional even when the network service failed.

---

## 📄 License

This project is licensed under the Apache 2.0 License - see the [LICENSE](LICENSE) file for details.
