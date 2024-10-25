# User Access Management System

This project is a simple web application that allows users to register, request access to software applications, and enables managers to approve or reject access requests. It is built using **Java Servlets**, **JSP**, **PostgreSQL**, and **Maven**.

## Features
- **User Registration**: Employees can sign up with a default role.
- **Login System**: Registered users can log in based on their role.
- **Software Management**: Admins can add new software applications.
- **Access Requests**: Employees can request access to software.
- **Approval System**: Managers can approve or reject access requests.

## Technologies Used
- **Java Servlets**
- **JSP (JavaServer Pages)**
- **PostgreSQL Database**
- **Maven** for project management

## Prerequisites
- **JDK 8** or higher
- **Apache Tomcat 9** or higher
- **PostgreSQL** database
- **Maven** installed
- **Eclipse IDE** (or any IDE that supports Java + Maven)

## Setup Instructions

### 1. Database Setup
1. Install and configure PostgreSQL.
2. Create a database named `access_management`.
3. Run the following script to create the necessary tables:

   ```sql
   CREATE TABLE users (
       id SERIAL PRIMARY KEY,
       username VARCHAR(255) UNIQUE,
       password VARCHAR(255),
       role VARCHAR(50)
   );

   CREATE TABLE software (
       id SERIAL PRIMARY KEY,
       name VARCHAR(255),
       description TEXT,
       access_levels TEXT
   );

   CREATE TABLE requests (
       id SERIAL PRIMARY KEY,
       user_id INT REFERENCES users(id),
       software_id INT REFERENCES software(id),
       access_type VARCHAR(50),
       reason TEXT,
       status VARCHAR(50)
   );

   ## 2. Project Setup

1. **Download the project**:
   - Download the zip file from [here](#).
   - Extract the project files.

2. **Open the project in Eclipse**:
   - Open **Eclipse IDE**.
   - Click on `File -> Import -> Maven -> Existing Maven Projects`.
   - Select the folder where the project was extracted.
   - Click `Finish`.

3. **Configure PostgreSQL Database**:
   - Open `SignUpServlet.java` (and other servlets if needed).
   - Update the database credentials:
     ```java
     private static final String DB_URL = "jdbc:postgresql://localhost:5432/access_management";
     private static final String DB_USER = "your_db_user";
     private static final String DB_PASSWORD = "your_db_password";
     ```

4. **Run the project**:
   - Right-click on the project in Eclipse and choose `Run As -> Run on Server`.
   - Select Apache Tomcat as your server and deploy the project.

5. **Access the application**:
   - Open a browser and go to `http://localhost:8080/UserAccessManagementSystem/` to see the application.
   - Use the **Sign Up** page to create a new user.

## 3. Testing the Application
- **Sign Up**: Go to `/signup.jsp` to register a new employee.
- **Login**: Use `/login.jsp` to log in as an employee, manager, or admin.
- **Admin Functionality**: Admins can add new software.
- **Employee Requests**: Employees can request access to software.
- **Manager Approvals**: Managers can approve or reject access requests.

## Project Structure
- `src/main/java/com/yourcompany/accessmanagement`: Contains the Java Servlets.
- `src/main/webapp/jsp`: Contains the JSP files for front-end.
- `src/main/webapp/WEB-INF`: Contains `web.xml` for servlet configurations.
- `pom.xml`: Maven configuration file.


