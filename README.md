# 🚀 Java Tomcat Rest Engine

A full-featured Java REST API built with **Jersey (JAX-RS)**, deployed on **Apache Tomcat**, and backed by **JPA**, **PostgreSQL/MySQL**, **JWT security**, and **Maven**.  
Includes integration tests, Testcontainers, CDI, environment variable support, and a flexible WAR-based deployment flow.

<br>

## 🧰 Tech Stack

### Backend
![Java](https://img.shields.io/badge/Java_17-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white)
![Jakarta REST (JAX-RS)](https://img.shields.io/badge/JAX--RS-0066CC?style=for-the-badge&logo=rest&logoColor=white)
![Tomcat](https://img.shields.io/badge/Tomcat-F8DC75?style=for-the-badge&logo=apachetomcat&logoColor=black)
![Maven](https://img.shields.io/badge/Maven-C71A36?style=for-the-badge&logo=apachemaven&logoColor=white)

### Security
![JWT](https://img.shields.io/badge/JWT-000000?style=for-the-badge&logo=jsonwebtokens&logoColor=white)
![BCrypt](https://img.shields.io/badge/BCrypt-087CFA?style=for-the-badge&logo=security&logoColor=white)

### Persistence
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-316192?style=for-the-badge&logo=postgresql&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-00758F?style=for-the-badge&logo=mysql&logoColor=white)
![EclipseLink](https://img.shields.io/badge/EclipseLink-2C2255?style=for-the-badge&logo=eclipse&logoColor=white)

### Testing
![JUnit](https://img.shields.io/badge/JUnit_5-25A162?style=for-the-badge&logo=junit5&logoColor=white)
![REST Assured](https://img.shields.io/badge/REST_Assured-4B8BBE?style=for-the-badge&logo=swagger&logoColor=white)
![Testcontainers](https://img.shields.io/badge/Testcontainers-00A3E0?style=for-the-badge&logo=docker&logoColor=white)

### Logging
![SLF4J](https://img.shields.io/badge/SLF4J-000000?style=for-the-badge&logo=slf4j&logoColor=white)
![Logback](https://img.shields.io/badge/Logback-EB5C2A?style=for-the-badge&logoColor=white)

---

## 📌 Features

- JAX-RS REST API with Jersey  
- WAR deployment to Tomcat  
- JSON serialization via Jackson / Gson  
- CDI dependency injection (Weld)  
- JPA support (EclipseLink)  
- PostgreSQL + MySQL drivers included  
- JWT authentication (Nimbus JOSE)  
- Password hashing (BCrypt)  
- Environment variable loading (`dotenv-java`)  
- Integration tests with Testcontainers  
- REST Assured API tests  
- Logging via SLF4J + Logback  

---

## 📂 Project Structure

```

src/
├── main/java
│   ├── controllers/      # REST endpoints
│   ├── services/         # Business logic
│   ├── daos/             # Persistence layer
│   ├── security/         # JWT + BCrypt
│   ├── config/           # CDI, JPA, environment
│   └── Application.java  # Bootstrapping
│
└── test/java
├── integration/      # REST Assured + Testcontainers
└── unit/             # JUnit 5 tests

````

---

## 🚀 Getting Started

### 1. Build
```bash
mvn clean package
````

### 2. Deploy to Tomcat

Copy the generated `.war` file to:

```
$TOMCAT_HOME/webapps/
```

Or deploy via Maven plugin:

```bash
mvn tomcat7:deploy
```

### 3. Run tests

```bash
mvn test
```

---

## 🖼 Architecture Diagram (ASCII)

```
            ┌────────────────────┐
            │      Client        │
            └─────────┬──────────┘
                      │ HTTP (REST)
                      ▼
            ┌────────────────────┐
            │     Tomcat         │
            │   (Servlet API)    │
            └─────────┬──────────┘
                      │ dispatch
                      ▼
            ┌────────────────────┐
            │  Jersey JAX-RS      │
            │  Controllers        │
            └─────────┬──────────┘
                      │ calls
                      ▼
            ┌────────────────────┐
            │   Services Layer    │
            └─────────┬──────────┘
                      │ uses
                      ▼
            ┌────────────────────┐
            │       JPA           │
            │ (EclipseLink)       │
            └─────────┬──────────┘
                      │ connects
                      ▼
            ┌────────────────────┐
            │ PostgreSQL/MySQL   │
            └────────────────────┘
```

---

## 📜 License

MIT License.

---

## 🌐 **REST API / Server Technologies**

| Library                                                                                                   | Purpose                                          |
| --------------------------------------------------------------------------------------------------------- | ------------------------------------------------ |
| **Jersey (Glassfish JAX-RS)** — `jersey-container-servlet`, `jersey-media-json-jackson`, `jersey-cdi2-se` | Main REST framework providing JAX-RS annotations |
| **Jakarta Servlet API 6.0.0**                                                                             | Required by Tomcat / WAR deployment              |
| **Jersey Grizzly HTTP Container** (test scope)                                                            | Embedded HTTP server for integration tests       |
| **Gson**                                                                                                  | JSON serialization (alternative to Jackson)      |

---

## 🧩 **Dependency Injection**

| Library             | Purpose                            |
| ------------------- | ---------------------------------- |
| **Weld SE (CDI 2)** | CDI dependency injection container |

---

## 🔐 **Security**

| Library               | Purpose                                   |
| --------------------- | ----------------------------------------- |
| **Nimbus JOSE + JWT** | JWT token creation, parsing, verification |
| **jbcrypt**           | Password hashing                          |

---

## 🛢 **Database & Persistence**

| Library                        | Purpose                          |
| ------------------------------ | -------------------------------- |
| **PostgreSQL driver (42.6.0)** | PostgreSQL database connectivity |
| **MySQL Connector/J (8.0.32)** | MySQL database connectivity      |
| **EclipseLink JPA (3.0.2)**    | JPA ORM provider                 |

---

## 🧪 **Testing Stack**

| Library                               | Purpose                         |
| ------------------------------------- | ------------------------------- |
| **JUnit 5 (Jupiter)**                 | Unit testing                    |
| **Hamcrest**                          | Matcher library                 |
| **REST Assured**                      | HTTP API integration testing    |
| **Testcontainers Core**               | Containerized test environments |
| **Testcontainers MySQL, JDBC, JUnit** | DB container testing support    |

---

## 🔧 **Build & Deployment Tools**

| Technology                  | Purpose                       |
| --------------------------- | ----------------------------- |
| **Maven**                   | Build system                  |
| **Tomcat 7 Maven Plugin**   | Remote Tomcat deployment      |
| **Maven WAR Plugin**        | Creates `.war` package        |
| **Maven Compiler Plugin**   | Configures Java 17            |
| **Maven Surefire Plugin**   | Runs tests                    |
| **Properties Maven Plugin** | Writes POM properties to file |

---

## 📝 **Environment Handling**

| Library         | Purpose                                |
| --------------- | -------------------------------------- |
| **dotenv-java** | Load environment variables from `.env` |

---

## 📊 **Logging**

| Library                    | Purpose             |
| -------------------------- | ------------------- |
| **SLF4J API**              | Logging abstraction |
| **Logback Classic + Core** | Logging backend     |

---

## 🖥 **JDK**

* **Java 17**

---

