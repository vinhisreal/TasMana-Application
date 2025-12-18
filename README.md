# TasMana - Building & Condominium Management System

[![.NET](https://img.shields.io/badge/.NET-8.0-512BD4?logo=dotnet)](https://dotnet.microsoft.com/)
[![C#](https://img.shields.io/badge/C%23-11.0-239120?logo=c-sharp)](https://docs.microsoft.com/en-us/dotnet/csharp/)
[![SQL Server](https://img.shields.io/badge/SQL%20Server-2019-CC2927?logo=microsoft-sql-server)](https://www.microsoft.com/en-us/sql-server)
[![Entity Framework](https://img.shields.io/badge/EF%20Core-8.0-512BD4)](https://docs.microsoft.com/en-us/ef/core/)

A comprehensive building and condominium management system built with **C# .NET** using a **3-Tier Architecture**. The system supports resident management, human resources, task assignment, and building-related business operations.

## 📋 Table of Contents

- [Features](#-features)
- [Architecture](#-architecture)
- [Tech Stack](#-tech-stack)
- [Project Structure](#-project-structure)
- [Getting Started](#-getting-started)
- [Configuration](#-configuration)
- [Usage](#-usage)
- [Database Schema](#-database-schema)
- [Contributing](#-contributing)
- [License](#-license)

## ✨ Features

### 🏠 Resident Management
- Manage resident information (Homeowners, Residents, Tenants)
- Apartment management with detailed information
- Authorized person management
- Commercial tenant management

### 👥 Human Resources Management
- Employee management by department and group
- Manager and CEO management
- Role-based access control
- Account management and authentication

### 📋 Task Management
- Task assignment and delegation
- Progress tracking
- Deadline management with automatic notifications
- PDF file attachment upload/download
- Task statistics and reporting

### 🏢 Organization Management
- Department management (PhongBan)
- Group management (Nhom)
- Work area management

### 🤖 Automation System
- **Cronjob**: Automatic email reminders for upcoming deadlines
- Email notifications for employees and task assigners
- PDF file validation

## 🏗️ Architecture

The project is built using **3-Tier Architecture**:

### Repositories Layer (Data Access Layer)
- Entity Framework Core with SQL Server
- Repository Pattern for database operations
- Stored Procedures for complex business logic

### Services Layer (Business Logic Layer)
- Business logic processing
- Validation and business rules
- Integration with Mail, Download, and Weather services

### UIs Layer (Presentation Layer)
- Windows Forms Application
- Session and authentication management
- Role-based authorization (CEO, Manager, Employee, Resident)

## 🛠️ Tech Stack

### Backend
- **C# .NET 8.0**
- **Entity Framework Core** - ORM framework
- **SQL Server** - Database
- **Microsoft.Extensions.Configuration** - Configuration management
- **Stored Procedures** - Database query optimization

### Frontend
- **Windows Forms** - Desktop application UI
- **Custom Components** - Custom component library

### Services & Utilities
- **Mail Service** - Email notification system
- **Download Service** - File upload/download management
- **Weather Service** - Weather information integration
- **Cronjob** - Automated scheduled tasks (task reminders)

### Libraries & Tools
- **EPPlus** - Excel file processing
- **iTextSharp** - PDF file processing
- **IronPython** - Python script integration
- **Microsoft Office Interop** - Microsoft Office integration

## 📦 Project Structure

```
TasMana-Application/
├── Repositories/          # Data Access Layer
│   ├── Entities/          # Entity models (EF Core)
│   ├── Utilities/         # Database utilities
│   └── *Repository.cs     # Repository classes
├── Services/              # Business Logic Layer
│   └── *Service.cs        # Service classes
├── UIs/                   # Presentation Layer
│   ├── CustomComponent/   # Custom UI components
│   ├── Resources/         # Images and resources
│   └── *.cs               # Form classes
└── Cronjob/               # Scheduled tasks
    └── Program.cs         # Cronjob implementation
```

## 🚀 Getting Started

### Prerequisites

- [.NET 8.0 SDK](https://dotnet.microsoft.com/download/dotnet/8.0)
- [SQL Server](https://www.microsoft.com/en-us/sql-server/sql-server-downloads) (Express or Standard)
- [Visual Studio 2022](https://visualstudio.microsoft.com/) or [Visual Studio Code](https://code.visualstudio.com/)

### Installation

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd TasMana-Application
   ```

2. **Configure Database**
   - Create `TasMana` database on SQL Server
   - Update connection string in `UIs/appsettings.json`
   ```json
   {
     "ConnectionStrings": {
       "DBDefault": "Server=YOUR_SERVER;Database=TasMana;Integrated Security=True;TrustServerCertificate=True;"
     }
   }
   ```

3. **Restore NuGet Packages**
   ```bash
   dotnet restore
   ```

4. **Build Solution**
   ```bash
   dotnet build
   ```

5. **Run Application**
   ```bash
   cd UIs
   dotnet run
   ```

## ⚙️ Configuration

### Database Connection

Update the connection string in `UIs/appsettings.json`:

```json
{
  "ConnectionStrings": {
    "DBDefault": "Server=localhost;Database=TasMana;Integrated Security=True;TrustServerCertificate=True;"
  }
}
```

### Cronjob Configuration

The cronjob is configured to automatically send email reminders for tasks:
- Runs periodically to check upcoming deadlines
- Sends emails to employees and task assigners 5 days before deadline

Configure in `Cronjob/Program.cs` and schedule using Windows Task Scheduler.

### Email Service Configuration

Update email credentials in `Services/MailService.cs` or `Cronjob/Program.cs`:

```csharp
var fromAddress = new MailAddress("your-email@gmail.com");
const string frompass = "your-app-password";
```

## 📖 Usage

### Task Management Workflow

1. **Assign Task**: Manager/CEO creates and assigns tasks to employees
2. **Accept Task**: Employee receives and confirms the task
3. **Update Progress**: Employee updates task status
4. **Complete Task**: Mark task as completed
5. **Automatic Notification**: System automatically sends email reminders

### Role-Based Access

- **CEO**: Highest privileges, manages entire system
- **Manager**: Manages department and employees
- **Employee**: Performs and updates tasks
- **Resident**: Views information and requests services

## 📊 Database Schema

The system uses SQL Server with the following main tables:

- `NhanSu`, `NhanVien`, `QuanLi`, `CEO` - Human resources management
- `CuDan`, `ChuHo`, `CanHo` - Resident management
- `GiaoViec`, `NhanViec` - Task management
- `PhongBan`, `Nhom` - Organization management
- `KhuVucLamViec` - Work area management

## 🎯 Key Features

- ✅ Clean 3-tier architecture, maintainable and scalable
- ✅ Repository Pattern for data access separation
- ✅ Entity Framework Core for modern ORM
- ✅ Stored Procedures for optimal performance
- ✅ Automation with Cronjob
- ✅ PDF file management with validation
- ✅ Flexible role-based authorization system
- ✅ Automatic email notifications

## 🎓 Skills Demonstrated

This project demonstrates:
- **Backend Development**: C# .NET, Entity Framework Core, SQL Server
- **Software Architecture**: 3-Tier Architecture, Repository Pattern
- **Database Design**: Database schema design, Stored Procedures
- **Business Logic**: Complex business processing, workflow management
- **Automation**: Cronjob, email automation
- **File Processing**: PDF, Excel file handling

## 🔮 Future Development

- [ ] Migrate to ASP.NET Core Web API
- [ ] Build Frontend with ReactJS
- [ ] Integrate GraphQL API
- [ ] Integrate with ERP system (Odoo)
- [ ] Mobile application
- [ ] Real-time notifications
- [ ] Advanced reporting and analytics

## 🤝 Contributing

This project was developed by TDTU team. Contributions are welcome!

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 👥 Authors

- **TDTU Team** - *Initial work*

## 🙏 Acknowledgments

- Entity Framework Core team
- .NET community
- All contributors and supporters

---

**Note**: This is an academic/learning project developed for building and condominium management with complex business features similar to ERP systems.
