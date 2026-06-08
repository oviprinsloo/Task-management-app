# Task Management System
### A C++ Mini Project | Object-Oriented Programming + STL

---

## 📌 Overview

The Task Management System is a console-based C++ application that allows users to create, organize, prioritize, and track tasks efficiently. It demonstrates core Object-Oriented Programming principles and makes use of C++ Standard Template Library (STL) containers for optimal performance.

---

## 🎯 Objectives

- Apply OOP concepts: Classes, Inheritance, Polymorphism, Encapsulation
- Use STL containers: `std::unordered_map` and `std::priority_queue`
- Simulate a real-world task tracking system
- Practice clean code structure and modular design

---

## 🛠️ Technologies Used

| Technology | Purpose |
|------------|---------|
| C++ (C++17) | Core programming language |
| `std::unordered_map` | O(1) task storage and retrieval by ID |
| `std::priority_queue` | Sorting tasks by priority (max-heap) |
| `std::vector` | Internal container for priority queue |
| OOP (Classes & Inheritance) | Task type hierarchy |

---

## 🏗️ Project Structure

```
task_manager.cpp
│
├── Enums
│   ├── Priority       (LOW, MEDIUM, HIGH)
│   └── Status         (PENDING, IN_PROGRESS, DONE)
│
├── Classes
│   ├── Task           → Base class
│   ├── UrgentTask     → Inherits Task (always HIGH priority)
│   └── RecurringTask  → Inherits Task (pattern + occurrences)
│
└── TaskManager        → Core logic class
    ├── unordered_map<int, Task*>   → stores all tasks
    └── priority_queue<Task*, ...>  → used for priority view
```

---

## ✨ Features

| # | Feature | Description |
|---|---------|-------------|
| 1 | Add General Task | Create a task with title, description, priority, due date |
| 2 | Add Urgent Task | High-priority task with an escalation contact |
| 3 | Add Recurring Task | Repeating task with pattern (Daily/Weekly) and occurrence count |
| 4 | Delete Task | Remove a task by its ID |
| 5 | Update Status | Change task status: Pending → In Progress → Done |
| 6 | Update Priority | Change task priority: Low / Medium / High |
| 7 | View by ID | Display full details of a specific task |
| 8 | View All Tasks | List every task in the system |
| 9 | View by Priority | Display tasks sorted High → Medium → Low using `priority_queue` |
| 10 | View by Status | Filter tasks by Pending / In Progress / Done |
| 11 | Search by Title | Keyword-based case-insensitive title search |
| 12 | Summary Dashboard | Count of tasks by status and priority |

---

## 🧠 OOP Concepts Demonstrated

### 1. Encapsulation
All task data (title, priority, status, etc.) is kept private/protected inside the `Task` class. Access is only through public getters and setters.

### 2. Inheritance
```
Task  (Base)
 ├── UrgentTask     → adds escalation contact
 └── RecurringTask  → adds recurrence pattern + occurrences
```

### 3. Polymorphism
`display()` and `getType()` are declared as `virtual` in `Task` and overridden in both subclasses — the correct version is called at runtime based on object type.

### 4. Abstraction
The `TaskManager` class hides all internal storage logic. The user interacts through a clean menu interface without knowing about `unordered_map` or heap internals.

---

## 📦 STL Usage Explained

### `std::unordered_map<int, Task*>`
- Stores all tasks with their ID as the key
- Provides **O(1) average** insert, delete, and lookup
- Chosen over `std::map` (O(log n)) for faster access

### `std::priority_queue<Task*, vector<Task*>, TaskComparator>`
- Max-heap structure — task with highest priority stays on top
- Built dynamically when "View by Priority" is selected
- Uses a custom comparator `TaskComparator` based on priority enum value

---

## ▶️ How to Run

### Prerequisites
- g++ compiler with C++17 support

### Compile
```bash
g++ -std=c++17 task_manager.cpp -o task_manager
```

### Run
```bash
./task_manager        # Linux / Mac
task_manager.exe      # Windows
```

---

## 🖥️ Sample Output

```
  ╔══════════════════════════════════╗
  ║     TASK MANAGEMENT SYSTEM       ║
  ╠══════════════════════════════════╣
  ║  1. Add General Task             ║
  ║  2. Add Urgent Task              ║
  ...

  Tasks by Priority (Highest → Lowest):
  ---------------------------------------------
  ID       : 2
  Type     : Urgent
  Title    : Fix Login Bug
  Priority : High
  Status   : Pending
  Due Date : 2025-04-20
  Escalate : team-lead@company.com
  ---------------------------------------------
```

---

## 📊 Sample Summary Dashboard

```
  ╔══════════════════════════╗
  ║     TASK SUMMARY         ║
  ╠══════════════════════════╣
  ║ Total Tasks   : 5        ║
  ╠══════════════════════════╣
  ║ Pending       : 4        ║
  ║ In Progress   : 1        ║
  ║ Done          : 0        ║
  ╠══════════════════════════╣
  ║ High Priority : 2        ║
  ║ Med Priority  : 2        ║
  ║ Low Priority  : 1        ║
  ╚══════════════════════════╝
```

---

## 🔮 Possible Future Enhancements

- File I/O — save and load tasks from a `.txt` or `.csv` file
- Due date alerts — flag tasks past their deadline
- User authentication — multi-user task boards
- GUI — integrate with a graphics library (SFML / Qt)

---

## 👩‍💻 Author

**Ovi**
B.E. Computer and Communication Engineering
Sri Eshwar College of Engineering

---

## 📄 License

This project is developed for academic purposes as part of the C++ Mini Project coursework.
