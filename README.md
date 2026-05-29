# Student Record System (Django)

A web-based **Student Record System** built with **Django** and **MySQL**. It supports managing students, courses, subjects, profiles, and related records through a browser UI.

## Prerequisites

- **Python** 3.10+ (3.11+ recommended)
- **MySQL** (the project was developed with [XAMPP](https://www.apachefriends.org/) on Windows; any local MySQL/MariaDB server works)
- A terminal (PyCharm terminal, VS Code terminal, or system shell)

## Project structure

```
Student-Record-System-Django/
├── SQL File/
│   └── srspythondb.sql          # Database dump — import this into MySQL
├── studentrs/
│   ├── studentrecordsys/        # Django project (run commands from here)
│   │   ├── manage.py
│   │   ├── srsapp/              # Main application
│   │   ├── studentrecordsys/    # Project settings
│   │   ├── templates/
│   │   └── static/
│   └── venv/                    # Optional bundled Windows virtualenv
└── Installation-Guide.docx      # Additional setup notes (if included)
```

## How to run

### 1. Get the project

Clone or download this repository, then open the folder on your machine.

If you received a **ZIP** archive:

1. Extract the archive.
2. Copy the **`studentrs`** folder to a convenient location (for example, your Desktop).

### 2. Set up MySQL

1. Start **MySQL** (via XAMPP Control Panel or your MySQL service).
2. Open **phpMyAdmin** or the MySQL client.
3. Create a database named **`srspythondb`**.
4. **Import** the SQL dump:
   - File: `SQL File/srspythondb.sql`
   - Target database: `srspythondb`

Default database settings used by the app (see `studentrs/studentrecordsys/studentrecordsys/settings.py`):

| Setting  | Value        |
|----------|--------------|
| Database | `srspythondb` |
| User     | `root`       |
| Password | *(empty)*    |
| Host     | `localhost`  |
| Port     | `3306`       |

If your MySQL `root` user has a password, update `PASSWORD` in `settings.py` to match.

### 3. Python environment

Create and activate a virtual environment, then install dependencies.

**Windows (PowerShell or CMD):**

```bash
cd path\to\studentrs
python -m venv venv
venv\Scripts\activate
pip install django==5.0.3 mysqlclient pillow
```

**Linux / macOS:**

```bash
cd path/to/studentrs
python3 -m venv venv
source venv/bin/activate
pip install django==5.0.3 mysqlclient pillow
```

> On Linux you may need system packages before `mysqlclient` installs, for example:  
> `sudo apt install python3-dev default-libmysqlclient-dev build-essential`

### 4. Run the development server

Navigate to the Django project directory (where `manage.py` lives):

```bash
cd studentrecordsys
python manage.py runserver
```

**Example (Windows):**

```bash
cd C:\Users\YourName\Desktop\studentrs\studentrecordsys
python manage.py runserver
```

### 5. Open the application

In your browser, go to:

**http://127.0.0.1:8000/**

The bundled database includes an admin user with username **`admin`**. Use the password provided with your project package or in `Installation-Guide.docx`. If you do not have it, reset the password:

```bash
python manage.py changepassword admin
```

## Optional: Django admin

Django’s built-in admin is available if you use a superuser account:

**http://127.0.0.1:8000/admin/**

## Troubleshooting

| Issue | What to try |
|-------|-------------|
| `Can't connect to MySQL server` | Start MySQL in XAMPP (or your service). Confirm host/port in `settings.py`. |
| `Access denied for user 'root'` | Set the correct `PASSWORD` in `settings.py`. |
| `No module named 'MySQLdb'` | Run `pip install mysqlclient` inside your active virtualenv. |
| `Unknown database 'srspythondb'` | Create the database and import `SQL File/srspythondb.sql`. |
| Port 8000 in use | Run `python manage.py runserver 8080` and open `http://127.0.0.1:8080/`. |

## Tech stack

- **Django** 5.0.3  
- **MySQL** / MariaDB  
- **Pillow** (image uploads for profiles)

## License

This project is licensed by MIT.
