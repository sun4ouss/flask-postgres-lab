# Flask PostgreSQL Lab

A simple Flask web application with user authentication and PostgreSQL database integration, ready for deployment on Render.

## Features

- User registration and authentication
- Secure password hashing
- PostgreSQL database integration
- Responsive Bootstrap 5 UI
- Flash messages for user feedback
- Protected routes

## Prerequisites

- Python 3.8+
- PostgreSQL database (local or remote)
- pip (Python package installer)

## Local Development Setup

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd flask_postgres_lab
   ```

2. **Create and activate a virtual environment**
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: .\venv\Scripts\activate
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **Set up environment variables**
   Create a `.env` file in the root directory with the following content:
   ```
   FLASK_APP=app.py
   FLASK_ENV=development
   SECRET_KEY=your-secret-key-here
   DATABASE_URL=postgresql://username:password@localhost:5432/flask_db
   ```
   Replace the values with your actual database credentials.

5. **Initialize the database**
   Run the following commands in a Python shell:
   ```python
   from app import app, db
   with app.app_context():
       db.create_all()
   ```

6. **Run the development server**
   ```bash
   flask run
   ```
   The application will be available at `http://localhost:5000`

## Deployment to Render

1. **Create a new Web Service**
   - Go to [Render Dashboard](https://dashboard.render.com/)
   - Click "New" and select "Web Service"
   - Connect your GitHub/GitLab repository or use the public repository URL

2. **Configure the service**
   - Name your service (e.g., "flask-postgres-lab")
   - Select "Docker" as the runtime
   - Choose your region
   - Select the free plan
   - Add the following environment variables:
     - `PYTHON_VERSION`: 3.9.0
     - `FLASK_APP`: app.py
     - `SECRET_KEY`: Generate a secure secret key
     - `DATABASE_URL`: Your PostgreSQL database URL (you can use Render's managed PostgreSQL)

3. **Deploy**
   - Click "Create Web Service"
   - Render will automatically build and deploy your application

## Database Setup

### Local PostgreSQL
1. Install PostgreSQL on your system
2. Create a new database:
   ```bash
   createdb flask_db
   ```
3. Update the `DATABASE_URL` in your `.env` file

### Render PostgreSQL (Recommended for Deployment)
1. In the Render Dashboard, go to "New" > "PostgreSQL"
2. Configure your database (name, database, user, etc.)
3. Copy the external database URL and add it to your environment variables

## Project Structure

```
flask_postgres_lab/
├── app.py                # Main application file
├── requirements.txt      # Python dependencies
├── Procfile             # For deployment configuration
├── .env                 # Environment variables (not version controlled)
├── .gitignore
├── README.md
└── templates/           # HTML templates
    ├── base.html        # Base template
    ├── index.html       # Home page
    ├── login.html       # Login page
    ├── register.html    # Registration page
    └── dashboard.html   # User dashboard
```

## Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
