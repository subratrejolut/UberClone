# UberClone Backend API

This is the backend API for the UberClone application, built using Node.js, Express, and MongoDB. It handles user authentication, registration, and other backend functionalities.

## Table of Contents

- [Installation](#installation)
- [Environment Variables](#environment-variables)
- [Available Endpoints](#available-endpoints)
  - [User Registration](#user-registration)
- [Example Responses](#example-responses)
- [Dependencies](#dependencies)
- [License](#license)

---

## Installation

1.  Clone the repository:

    `git clone https://github.com/your-repo/UberClone.git`

    `cd UberClone/Backend`

2.  Install dependencies:

    `npm install`

3.  Start the server:

    `npm start`

4.  Environment Variables

    > Create a .env file in the root directory and configure the following keys:

    `PORT=5000`

    `MONGO_URI=your_mongo_database_url`

    `JWT_SECRET=your_jwt_secret_key`

    > Replace your_mongo_database_url and your_jwt_secret_key with appropriate values for your setup.

5.  Available Endpoints

    > User Registration

    `POST /api/users/register`

    > This endpoint registers a new user.

6.  Request Body

        {
          "fullname": {
            "firstname": "John",
            "lastname": "Doe"
          },
          "email": "johndoe@example.com",
          "password": "password123"
        }

    Validation Rules

        email: Must be a valid email address.
        fullname.firstname: Must be at least 3 characters long.
        password: Must be at least 6 characters long.

    Headers

    > No authorization is required for this endpoint.

7.  Example Responses
    Successful Registration
    Status Code: 201 Created

        {
          "user": {
            "\_id": "64b8a42e917df23bc9f3",
            "fullname": {
            "firstname": "John",
            "lastname": "Doe"
          },
          "email": "johndoe@example.com",
          "socketId": null,
          "\_\_v": 0
          },
          "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9..."
          }


        Validation Error:

        (Status Code: 400 Bad Request)

          {
          "errors": [
            {
              "msg": "Invalid email",
              "param": "email",
              "location": "body"
            },
            {
              "msg": "First name must be at least 3 characters long",
              "param": "fullname.firstname",
              "location": "body"
            }
          ]
        }

## Dependencies

    1. Express: Fast, unopinionated, minimalist web framework.
    2. Mongoose: MongoDB object modeling tool.
    3. bcrypt: Library to hash passwords.
    4. jsonwebtoken: Tool to securely sign and verify tokens.
    5. express-validator: Middleware for validating request payloads.

## License

> This project is licensed under the MIT License.
