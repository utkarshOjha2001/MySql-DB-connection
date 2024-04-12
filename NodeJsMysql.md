# Node.js CRUD Operations with MySQL

This guide will walk you through the steps to connect to a MySQL database using Node.js and perform CRUD (Create, Read, Update, Delete) operations.

## Prerequisites

- Node.js installed on your system. If not installed, download and install it from [here](https://nodejs.org/).
- MySQL Server installed and running on your system or accessible remotely.

## Installation

1. Clone or download this repository.

2. Install dependencies using npm:

    ```bash
    npm install
    ```

3. Configure your MySQL connection settings in the `config.js` file.

## Connecting to MySQL Database

Ensure your MySQL Server is running, and then follow these steps:

1. Create  `config.js` file.

2. Update the following fields with your MySQL connection details:

    ```javascript
    const config = {
        host: 'your_mysql_host',
        user: 'your_mysql_username',
        password: 'your_mysql_password',
        database: 'your_mysql_database'
    };

    module.exports = config;
    ```

3. Save the `config.js` file.

## Performing CRUD Operations

The project comes with examples of CRUD operations using Node.js.

### 1. Create a Record (`create.js`)

```javascript
const mysql = require('mysql');
const config = require('./config');

const connection = mysql.createConnection(config);

// Connect to MySQL
connection.connect((err) => {
    if (err) throw err;
    console.log('Connected to MySQL database...');
});

// Insert a new record
const newRecord = { name: 'John Doe', email: 'john@example.com' };
connection.query('INSERT INTO users SET ?', newRecord, (err, result) => {
    if (err) throw err;
    console.log('New record inserted:', result.insertId);
});

// Close connection
connection.end((err) => {
    if (err) throw err;
    console.log('Connection closed.');
});

```
### 2. Read Records ('read.js')

```javascript

const mysql = require('mysql');
const config = require('./config');

const connection = mysql.createConnection(config);

// Connect to MySQL
connection.connect((err) => {
    if (err) throw err;
    console.log('Connected to MySQL database...');
});

// Retrieve records
connection.query('SELECT * FROM users', (err, results) => {
    if (err) throw err;
    console.log('Retrieved records:');
    console.log(results);
});

// Close connection
connection.end((err) => {
    if (err) throw err;
    console.log('Connection closed.');
});

```
### 3. Update a Record ('update.js')

```javascript

const mysql = require('mysql');
const config = require('./config');

const connection = mysql.createConnection(config);

// Connect to MySQL
connection.connect((err) => {
    if (err) throw err;
    console.log('Connected to MySQL database...');
});

// Update a record
const updatedRecord = { name: 'Jane Doe', email: 'jane@example.com' };
connection.query('UPDATE users SET ? WHERE id = ?', [updatedRecord, 1], (err, result) => {
    if (err) throw err;
    console.log('Record updated:', result.affectedRows);
});

// Close connection
connection.end((err) => {
    if (err) throw err;
    console.log('Connection closed.');
});

```

### 4. Delete a Record ('delete.js')

```javascript
const mysql = require('mysql');
const config = require('./config');

const connection = mysql.createConnection(config);

// Connect to MySQL
connection.connect((err) => {
    if (err) throw err;
    console.log('Connected to MySQL database...');
});

// Delete a record
connection.query('DELETE FROM users WHERE id = ?', [1], (err, result) => {
    if (err) throw err;
    console.log('Record deleted:', result.affectedRows);
});

// Close connection
connection.end((err) => {
    if (err) throw err;
    console.log('Connection closed.');
});
```

Replace users with your actual table name, and adjust the field names and values accordingly. These scripts should be run in your Node.js environment.

### Conclusion
With these steps, you should be able to connect to a MySQL database using Node.js and perform CRUD operations efficiently.


