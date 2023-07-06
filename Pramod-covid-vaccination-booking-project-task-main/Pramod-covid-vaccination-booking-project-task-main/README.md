# CovidVaccination-Booking
A Web Application for covid vaccination booking using Flask framework.

---------------------------------------------------------------------------------------------------------------------------

# BACKEND DEVELOPMENT CODING TASK (COVID VACCINATION BOOKING )

Create a web application for covid vaccination booking. Use any tech stack for the backend and db. A console-based application would work. Submissions with a very basic UI will be given extra marks.

## Type of Users
a. User
b. Admin

## User Use Cases

1. **Login**
2. **Sign up**
3. **Searching for Vaccination Centre and working hours**
4. **Apply for a vaccination slot (only 10 candidates allowed per day)**
5. **Logout**

## Admin Use Cases

1. **Login (Separate login for Admin)**
2. **Add Vaccination Centres**
3. **Get dosage details (group by centers)**
4. **Remove vaccination centres**

-------------------------------------------------------------------------------------------------------------------------

# TODO List for COVID Vaccination Booking Web Application

## Backend Setup
1. Create a new Replit project for your application.
2. Initialize a new Git repository in your Replit project.
3. Connect your Replit project to a GitHub repository for backup and version control.
4. Set up a virtual environment for the project.
   - Run the command: `python3 -m venv venv`
   - Activate the virtual environment:
     - For Windows: `venv\Scripts\activate`
     - For Linux/Mac: `source venv/bin/activate`
5. Install Flask and SQLite packages in the virtual environment:
   - Run the command: `pip install flask sqlite3`

## Database Setup
1. Create a new file called `database.py` in your Replit project.
2. Import the required packages (`sqlite3`).
3. Create a connection to the SQLite database and a cursor object.
4. Write SQL queries to create the necessary tables for the application.

      ### Admin Table

      - **Name**: The name of the admin.
      - **Email**: The email address of the admin.
      - **id (Primary Key)**: Unique identifier for the admin.
      - **Password**: The password associated with the admin's account.
      - **OTP (Number)**: One-time password used for authentication.

      ### User Table

      - **Name**: The name of the user.
      - **Email**: The email address of the user.
      - **id (Primary Key)**: Unique identifier for the user.
      - **Password**: The password associated with the user's account.
      - **OTP (Number)**: One-time password used for authentication.

      ### Vaccination Center

      - **Center id (Primary Key)**: Unique identifier for the vaccination center.
      - **Email-Id (Admin Foreign Key)**: Foreign key referencing the admin table's email id.
      - **Place**: The location or address of the vaccination center.
      - **Center Name**: The name of the vaccination center.
      - **Dosage (Number)**: The dosage number associated with the vaccination center.
      - **Working Hour**: The operating hours of the vaccination center.

      ### Vaccination Slots

      - **Slot id (Primary Key)**: Unique identifier for the vaccination slot.
      - **Center - Id (Foreign Key)**: Foreign key referencing the vaccination center table's center id.
      - **Slot Date (Date)**: The date of the vaccination slot.
      - **Available Slot (Number with Constraint max 10)**: The number of available slots for vaccination, with a maximum limit of 10.
      - **Email-Id (User Foreign Key)**: Foreign key referencing the user table's email id.

      ### User History

      - **Booking id (Primary Key)**: Unique identifier for the booking history.
      - **Email - Id (User Foreign Key)**: Foreign key referencing the user table's email id.
      - **Slot Id (Foreign Key)**: Foreign key referencing the vaccination slots table's slot id.
      - **Center Id (Foreign Key)**: Foreign key referencing the vaccination center table's center id.
      - **Slot Date (Foreign Key)**: Foreign key referencing the vaccination slots table's slot date.

5. Commit the changes and push them to your GitHub repository for backup.

## Rough Database Schema 

![image](https://github.com/pramod9951/Pramod-covid-vaccination-booking-project-task/assets/87662603/34e00c6d-6dfb-4d4f-9f97-922386293e27)


## Rough Wireframe for Each Page
1. Home.html
   ![image]<img width="905" alt="pramod admin page" src="https://github.com/pramod9951/Pramod-covid-vaccination-booking-project-task/assets/87662603/fb9405c9-abd8-4edd-a639-5dafbec8e628">
2. Sign-Up.html
   ![image]
   <img width="917" alt="pramod4" src="https://github.com/pramod9951/Pramod-covid-vaccination-booking-project-task/assets/87662603/5f85d00c-06d7-485c-a68b-03f1677194af">
3. Sign-In.html / Admin-Login.html
   ![image]<img width="919" alt="pramod 2" src="https://github.com/pramod9951/Pramod-covid-vaccination-booking-project-task/assets/87662603/cb4a333c-ee0b-46c0-a5b9-6673bf5adf98">
<img width="928" alt="pramod sign uo" src="https://github.com/pramod9951/Pramod-covid-vaccination-booking-project-task/assets/87662603/d06c55c4-f629-48e5-92c9-025a7361ffce">
<img width="917" alt="pramod4" src="https://github.com/pramod9951/Pramod-covid-vaccination-booking-project-task/assets/87662603/5f85d00c-06d7-485c-a68b-03f1677194af">
4. Book-Slots.html
   ![image]<img width="907" alt="pramod3" src="https://github.com/pramod9951/Pramod-covid-vaccination-booking-project-task/assets/87662603/50459446-7a36-42a3-8db4-f9132bf06180">

5. Admin-Dashboard.html
   ![image]<img width="908" alt="pramod5" src="https://github.com/pramod9951/Pramod-covid-vaccination-booking-project-task/assets/87662603/80fd4dc1-b768-41f1-83b7-5d734fc956d5">
   
## Flask App Setup
1. Create a new file called `app.py` in your Replit project.
2. Import the required packages (`flask`, `sqlite3`).
3. Initialize a Flask application object.
4. Create a route for the home page ('/') and a function to render it.
5. Create routes and functions for user-related use cases:
   - Sign up ('/signup')
   - Login ('/login')
   - Searching for Vaccination Centre and working hours ('/search')
   - Apply for a vaccination slot ('/apply')
   - Logout ('/logout')
6. Create routes and functions for admin-related use cases:
   - Admin login ('/admin/login')
   - Add Vaccination Centres ('/admin/add_centre')
   - Get dosage details ('/admin/dosage_details')
   - Remove vaccination centres ('/admin/remove_centre')
7. Run the Flask application:
   - Set the `FLASK_APP` environment variable: `export FLASK_APP=app.py`
   - Start the server: `flask run`

## User-related Functionality
1. Implement the sign-up functionality.
   - Create a template file called `signup.html` in your Replit project.
   - Define a function in `app.py` to handle the sign-up route.
   - Extract the form data from the request and insert it into the User table in the database.
2. Implement the login functionality.
   - Create a template file called `login.html` in your Replit project.
   - Define a function in `app.py` to handle the login route.
   - Verify the user's credentials against the User table in the database.
3. Implement the searching functionality.
   - Create a template file called `search.html` in your Replit project.
   - Define a function in `app.py` to handle the search route.
   - Retrieve the vaccination centers and their working hours from the VaccinationCenter table.
   - Pass the data to the template for rendering.
4. Implement the slot application functionality.
   - Create a template file called `apply.html` in your Replit project.
   - Define a function in `app.py` to handle the apply route.
   - Retrieve the selected vaccination center and date from the request.
   - Check if the slot capacity for the selected date is available and update the Slot table accordingly.
   - Display a success message or an error message to the user.
5. Implement the logout functionality.
   - Define a function in `app.py` to handle the logout route.
   - Clear the user's session data and redirect them to the login page.

## Admin-related Functionality
1. Implement the admin login functionality.
   - Create a template file called `admin_login.html` in your Replit project.
   - Define a function in `app.py` to handle the admin login route.
   - Verify the admin's credentials against a separate table in the database.
2. Implement the vaccination center addition functionality.
   - Create a template file called `add_centre.html` in your Replit project.
   - Define a function in `app.py` to handle the add center route.
   - Extract the form data from the request and insert it into the VaccinationCenter table in the database.
3. Implement the dosage details functionality.
   - Create a template file called `dosage_details.html` in your Replit project.
   - Define a function in `app.py` to handle the dosage details route.
   - Retrieve the dosage details by grouping the Slot table based on vaccination centers.
   - Pass the data to the template for rendering.
4. Implement the vaccination center removal functionality.
   - Create a template file called `remove_centre.html` in your Replit project.
   - Define a function in `app.py` to handle the remove center route.
   - Delete the selected vaccination center from the VaccinationCenter table in the database.
5. Secure admin routes.
   - Use decorators or middleware to restrict access to admin-related routes only for authenticated admin users.

## UI Improvements
1. Create HTML templates for all the routes mentioned in the previous steps and store them in your Replit project.
2. Style the templates using CSS to provide a better user experience.
3. Add appropriate form validations on the frontend using JavaScript.

## Testing and Deployment
1. Test the application by running it in your Replit project and going through all the use cases.
2. Once the application is working as expected, commit and push the final changes to your GitHub repository.
3. Set up automatic deployment from your GitHub repository to Replit.
4. Monitor the deployed application for any errors or issues and make necessary adjustments if required.

Note: The above steps may change with respect to the changes in the websites to implement the COVID Vaccination Booking Web Application. It is recommended to refer to Flask, SQLite and Replit documentation for more detailed information on how to implement each step.
