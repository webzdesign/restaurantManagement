# Restaurant Management System

A Laravel-based web application framework with user authentication system. This project provides a foundation for building restaurant management features.

## Project Overview

This is a Laravel 8 application that includes a complete authentication system out of the box. The project serves as a starting point for developing restaurant management functionality, with user registration, login, password reset, and email verification capabilities already implemented.

## Tech Stack

### Backend
- **PHP**: ^7.3
- **Laravel Framework**: ^8.0
- **Laravel UI**: ^2.3 (Bootstrap scaffolding)

### Frontend
- **Bootstrap**: ^4.0.0
- **Vue.js**: ^2.5.17
- **jQuery**: ^3.2
- **Axios**: ^0.19
- **Sass**: ^1.20.1
- **Laravel Mix**: ^5.0.1 (Asset compilation)

### Development Tools
- **PHPUnit**: ^9.3 (Testing framework)
- **Laravel Tinker**: ^2.0 (REPL)
- **Guzzle HTTP**: ^7.0.1 (HTTP client)

## Folder Structure

```
restaurantManagement-master/
├── app/                          # Application core
│   ├── Console/                  # Artisan commands & scheduled tasks
│   ├── Exceptions/               # Exception handlers
│   ├── Http/                     # HTTP layer
│   │   ├── Controllers/          # Application controllers
│   │   │   └── Auth/             # Authentication controllers
│   │   └── Middleware/           # HTTP middleware
│   ├── Models/                   # Eloquent models
│   └── Providers/                # Service providers
├── bootstrap/                    # Application bootstrap files
├── config/                       # Configuration files
├── database/                     # Database related files
│   ├── factories/                # Model factories
│   ├── migrations/               # Database migrations
│   └── seeders/                  # Database seeders
├── public/                       # Public assets & entry point
├── resources/                    # Views, assets, language files
│   ├── css/                      # Compiled CSS
│   ├── js/                       # JavaScript files
│   ├── sass/                     # Sass source files
│   └── views/                    # Blade templates
│       ├── auth/                 # Authentication views
│       └── layouts/              # Layout templates
├── routes/                       # Route definitions
│   ├── api.php                   # API routes
│   ├── web.php                   # Web routes
│   └── console.php               # Console routes
├── storage/                       # Storage directory
└── tests/                        # Test files
```

## Feature List

### Authentication & Authorization
- User registration with email and password
- User login with remember me functionality
- Password reset via email
- Email verification
- Password confirmation
- Protected routes with authentication middleware
- Guest-only routes (login, register)

### User Management
- User model with email verification support
- Password hashing and encryption
- Remember token functionality
- User profile display

### Frontend
- Responsive Bootstrap 4 UI
- Vue.js components support
- Blade templating engine
- Asset compilation with Laravel Mix

## Application Flow

### Authentication Flow
1. **Registration**: User visits `/register` → fills form → account created → email verification sent
2. **Login**: User visits `/login` → enters credentials → authenticated → redirected to `/home`
3. **Password Reset**: User clicks "Forgot Password" → enters email → receives reset link → sets new password
4. **Email Verification**: User receives verification email → clicks link → email verified

### Request Flow
```
Request → Middleware → Route → Controller → Model → Database → Response
```

### Route Structure
- **Public Routes**: `/` (welcome page), `/login`, `/register`
- **Protected Routes**: `/home` (requires authentication)
- **API Routes**: `/api/user` (requires API authentication)

## API & Third-Party Integrations

### Current Integrations
- **None** - The application currently has no third-party API integrations configured.

### Available HTTP Client
- **Guzzle HTTP** is included in dependencies and can be used for API integrations.

## Setup & Installation Steps

### Prerequisites
- PHP >= 7.3
- Composer
- Node.js & NPM
- MySQL/PostgreSQL/SQLite
- Web server (Apache/Nginx) or PHP built-in server

### Installation

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd restaurantManagement-master
   ```

2. **Install PHP dependencies**
   ```bash
   composer install
   ```

3. **Install Node dependencies**
   ```bash
   npm install
   ```

4. **Environment configuration**
   ```bash
   cp .env.example .env
   php artisan key:generate
   ```

5. **Configure database**
   Edit `.env` file and set your database credentials:
   ```env
   DB_CONNECTION=mysql
   DB_HOST=127.0.0.1
   DB_PORT=3306
   DB_DATABASE=your_database_name
   DB_USERNAME=your_username
   DB_PASSWORD=your_password
   ```

6. **Run migrations**
   ```bash
   php artisan migrate
   ```

7. **Compile assets**
   ```bash
   npm run dev
   # or for production
   npm run production
   ```

## Environment Variables

Create a `.env` file in the root directory. Here's an example configuration:

```env
APP_NAME=Laravel
APP_ENV=local
APP_KEY=base64:your-generated-key
APP_DEBUG=true
APP_URL=http://localhost

LOG_CHANNEL=stack
LOG_LEVEL=debug

DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=restaurant_management
DB_USERNAME=root
DB_PASSWORD=

BROADCAST_DRIVER=log
CACHE_DRIVER=file
QUEUE_CONNECTION=sync
SESSION_DRIVER=file
SESSION_LIFETIME=120

REDIS_HOST=127.0.0.1
REDIS_PASSWORD=null
REDIS_PORT=6379

MAIL_MAILER=smtp
MAIL_HOST=smtp.mailtrap.io
MAIL_PORT=2525
MAIL_USERNAME=null
MAIL_PASSWORD=null
MAIL_ENCRYPTION=null
MAIL_FROM_ADDRESS=null
MAIL_FROM_NAME="${APP_NAME}"

AWS_ACCESS_KEY_ID=
AWS_SECRET_ACCESS_KEY=
AWS_DEFAULT_REGION=us-east-1
AWS_BUCKET=

PUSHER_APP_ID=
PUSHER_APP_KEY=
PUSHER_APP_SECRET=
PUSHER_APP_CLUSTER=mt1

MIX_PUSHER_APP_KEY="${PUSHER_APP_KEY}"
MIX_PUSHER_APP_CLUSTER="${PUSHER_APP_CLUSTER}"
```

## Running the Project

### Local Development

1. **Start the development server**
   ```bash
   php artisan serve
   ```
   The application will be available at `http://localhost:8000`

2. **Watch for asset changes** (in a separate terminal)
   ```bash
   npm run watch
   ```

3. **Access the application**
   - Welcome page: `http://localhost:8000`
   - Login: `http://localhost:8000/login`
   - Register: `http://localhost:8000/register`
   - Dashboard: `http://localhost:8000/home` (requires login)

### Production Deployment

1. **Set environment to production**
   ```env
   APP_ENV=production
   APP_DEBUG=false
   ```

2. **Optimize the application**
   ```bash
   php artisan config:cache
   php artisan route:cache
   php artisan view:cache
   ```

3. **Compile assets for production**
   ```bash
   npm run production
   ```

4. **Set proper file permissions**
   ```bash
   chmod -R 755 storage bootstrap/cache
   ```

## Cron Jobs / Background Tasks

### Current Scheduled Tasks
- **None configured** - The `app/Console/Kernel.php` file has no scheduled tasks defined.

### Setting Up Cron Jobs
To enable Laravel's task scheduler, add this to your server's crontab:
```bash
* * * * * cd /path-to-your-project && php artisan schedule:run >> /dev/null 2>&1
```

## Database Schema

### Users Table
- `id` - Primary key
- `name` - User's full name
- `email` - Unique email address
- `email_verified_at` - Email verification timestamp
- `password` - Hashed password
- `remember_token` - Remember me token
- `created_at` - Creation timestamp
- `updated_at` - Update timestamp

### Password Resets Table
- `email` - User email (indexed)
- `token` - Reset token
- `created_at` - Token creation timestamp

### Failed Jobs Table
- `id` - Primary key
- `uuid` - Unique identifier
- `connection` - Queue connection name
- `queue` - Queue name
- `payload` - Job payload
- `exception` - Exception details
- `failed_at` - Failure timestamp

## Common Use Cases

### Creating a New User
```php
use App\Models\User;

$user = User::create([
    'name' => 'John Doe',
    'email' => 'john@example.com',
    'password' => Hash::make('password'),
]);
```

### Accessing Authenticated User
```php
// In controllers
$user = auth()->user();

// In views
{{ Auth::user()->name }}
```

### Protecting Routes
```php
// In routes/web.php
Route::middleware('auth')->group(function () {
    Route::get('/dashboard', 'DashboardController@index');
});
```

## Known Limitations

1. **No Restaurant-Specific Features**: Despite the project name, no restaurant management features (menu, orders, tables, etc.) are currently implemented.

2. **Basic Authentication Only**: The application includes standard Laravel authentication without role-based access control or permissions system.

3. **No API Authentication**: While API routes exist, no token-based authentication (Sanctum/Passport) is configured.

4. **No Background Job Processing**: Queue system is configured but no jobs are implemented.

5. **No Email Configuration**: Mail settings need to be configured for password reset and email verification to work.

6. **No File Storage Configuration**: File uploads and storage are not configured.

## Future Improvements

Based on the project structure and naming, potential improvements include:

1. **Restaurant Management Features**
   - Menu management (categories, items, pricing)
   - Table/reservation management
   - Order processing system
   - Staff management
   - Inventory tracking

2. **Enhanced Authentication**
   - Role-based access control (Admin, Manager, Staff, Customer)
   - Multi-factor authentication
   - Social login integration

3. **API Development**
   - RESTful API for mobile apps
   - API authentication with Laravel Sanctum
   - API documentation with Swagger/OpenAPI

4. **Background Processing**
   - Order processing queues
   - Email notifications
   - Report generation

5. **Third-Party Integrations**
   - Payment gateway integration
   - SMS notifications
   - Analytics integration
   - POS system integration

6. **Testing**
   - Unit tests for models
   - Feature tests for controllers
   - Browser tests with Laravel Dusk

7. **Documentation**
   - API documentation
   - User guide
   - Developer documentation

## Contribution Guidelines

1. **Fork the repository** and create a feature branch
2. **Follow PSR-12 coding standards**
3. **Write meaningful commit messages**
4. **Add tests** for new features
5. **Update documentation** as needed
6. **Submit a pull request** with a clear description

### Code Style
- Follow Laravel conventions
- Use meaningful variable and function names
- Add comments for complex logic
- Keep functions focused and small

## License

This project is open-sourced software licensed under the [MIT license](https://opensource.org/licenses/MIT).

## Support

For issues, questions, or contributions, please open an issue on the repository.

---

**Note**: This is a foundational Laravel application. Restaurant management features need to be developed based on specific requirements.
