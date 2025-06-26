#Task-3(Writing Basic SELECT Queries)

# 📚 College Management System Database
This project demonstrates how to design and implement a relational database schema for a College Management System using SQL. It includes the Insertion, Updating and deleting of a data.

# 🔍 Project Overview
This database system is designed to manage:

- Using SELECT * and specific columns to display the data.
- Applying Different Conditions.
- Using Sort with ORDER BY.

The goal is to build a well-structured, normalized schema using SQL with clearly different CONDITIONS.

This project is part of my learning and internship submission, aimed at demonstrating my understanding of database design concepts.

#📌 Tables:
- Students
- Courses
- Enrollments

# 🧾 SQL Script
Creating the data
```
-- Create the database
CREATE DATABASE College;
USE College;

-- Create Students table
CREATE TABLE Students (
    StudentID INT PRIMARY KEY,
    Name VARCHAR(50) NOT NULL,
    Email VARCHAR(60) UNIQUE,
    DOB DATE
);

-- Create Courses table
CREATE TABLE Courses (
    CourseID INT PRIMARY KEY,
    CourseName VARCHAR(50) NOT NULL,
    Credits INT CHECK (Credits > 0)
);

-- Create Enrollments table
CREATE TABLE Enrollments (
    EnrollmentID INT PRIMARY KEY,
    StudentID INT,
    CourseID INT,
    EnrollmentDate DATE,
    FOREIGN KEY (StudentID) REFERENCES Students(StudentID),
    FOREIGN KEY (CourseID) REFERENCES Courses(CourseID)
);
```

Inserting the data
```
--Inserting the data in Student table

Insert into students (StudentID, Name, Email,DOB) 
values (1,'Prajjawal', 'kushwaha344@gmail.com','2002-07-20'),
(2,'khushi','khushi345@gmail.com','2000-08-23');

--Inserting the data in Courses table

Insert into Courses(CourseID,CourseName,Credits)
values(201,'Web Development',8),
(202,'SQL Developer',9);

--Inserting the data in Enrollment table

Insert into Enrollments(EnrollmentID,StudentID,CourseID,EnrollmentDate)
values(2001,1,202,'2025-06-23'),
(2002,2,201,'2025-06-12');
```

Updating the data
```
Update students set name ='Pranshu Sagar' where StudentID = 2;
```
Deleting the data
```
Delete from Enrollments where EnrollmentID=2002;
```

# Using SELECT to display the data
```
select * from students;
```
**For Specific column it uses**
```
select Name, DOB from students;
```

# Using Different Conditions
1-WHERE
```
select * from Enrollments where EnrollmentID<2002;
```
2-LIKE
```
select * from Courses where CourseName like 'w%' ;
```
3-BETWEEN, AND
```
select * from students where DOB between '2000-01-21' AND '2000-12-30';
```
4-OR
```
select * from Enrollments where CourseID=201 or CourseID=202;
```

# Using SORT BY
```
select * from Courses order by Credits desc;
```
```
select * from students order by DOB;
```
```
select * from Enrollments order by EnrollmentID;
```
