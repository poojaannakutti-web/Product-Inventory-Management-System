README.md


Product Inventory Management System
A backend-based Product Inventory Management System built with Node.js, Express.js, and MongoDB. The system provides role-based access control for managing products, inventory, suppliers, purchases, and users.

🚀 Features
User authentication using JWT

Role-based authorization

Product management

Inventory/stock management

Supplier management

Purchase management

Low-stock monitoring

Password hashing with bcrypt

MongoDB database integration

RESTful APIs

Environment-based configuration

Error handling and validation

👥 User Roles
Role	Responsibilities
Admin	Manage users, products, inventory, suppliers, purchases, and system settings
Inventory Manager	Manage products and monitor inventory
Sales Staff	View products and process sales
Purchase Manager	Manage suppliers and purchase orders
Warehouse Staff	Manage stock-in and stock-out operations
Viewer	View products, inventory, and reports

🛠️ Technology Stack
Node.js

Express.js

MongoDB

Mongoose

JWT

bcryptjs

dotenv

CORS

Nodemon

📁 Project Structure
product-inventory-management/
│
├── src/
│   ├── app.js
│   │
│   ├── config/
│   │   └── database.js
│   │
│   ├── controllers/
│   │   ├── authController.js
│   │   ├── productController.js
│   │   ├── inventoryController.js
│   │   ├── supplierController.js
│   │   ├── purchaseController.js
│   │   └── userController.js
│   │
│   ├── models/
│   │   ├── User.js
│   │   ├── Product.js
│   │   ├── Category.js
│   │   ├── Supplier.js
│   │   ├── Inventory.js
│   │   └── Purchase.js
│   │
│   ├── routes/
│   │   ├── authRoutes.js
│   │   ├── productRoutes.js
│   │   ├── inventoryRoutes.js
│   │   ├── supplierRoutes.js
│   │   ├── purchaseRoutes.js
│   │   └── userRoutes.js
│   │
│   ├── middleware/
│   │   ├── authMiddleware.js
│   │   └── roleMiddleware.js
│   │
│   └── services/
│       ├── inventoryService.js
│       └── productService.js
│
├── tests/
│   ├── auth.test.js
│   ├── product.test.js
│   └── inventory.test.js
│
├── .env
├── .env.example
├── .gitignore
├── package.json
└── README.md

⚙️ Installation
1. Clone the repository
git clone <repository-url>
cd product-inventory-management

2. Initialize the project
If package.json does not already exist:

npm init -y

3. Install dependencies
npm install express mongoose dotenv cors bcryptjs jsonwebtoken

Install the development dependency:

npm install --save-dev nodemon

🔐 Environment Configuration
Create a .env file in the project root:

PORT=5000
NODE_ENV=development

MONGODB_URI=mongodb://127.0.0.1:27017/product_inventory

JWT_SECRET=your_super_secret_jwt_key
JWT_EXPIRES_IN=7d

Do not commit .env to Git. Add it to .gitignore.

Example .gitignore:

node_modules/
.env

🗄️ Database
This project uses MongoDB.

Make sure MongoDB is running locally or provide a MongoDB Atlas connection string.

Local database:

mongodb://127.0.0.1:27017/product_inventory

Atlas example:

MONGODB_URI=mongodb+srv://<username>:<password>@<cluster>/<database>

▶️ Running the Application
Start the application in development mode:

npm run dev

Start the application normally:

npm start

The server will run at:

http://localhost:5000

📜 Package Scripts
Add the following scripts to package.json:

{
  "scripts": {
    "start": "node src/app.js",
    "dev": "nodemon src/app.js",
    "test": "jest"
  }
}

🔑 Authentication
The application uses JWT-based authentication.

Typical authentication flow:

User
  │
  ▼
Login
  │
  ▼
Validate Email & Password
  │
  ▼
Generate JWT
  │
  ▼
Client
  │
  ▼
Send JWT with API Requests
  │
  ▼
Authentication Middleware
  │
  ▼
Role Authorization
  │
  ▼
Protected Resource

Example request header:

Authorization: Bearer <your-jwt-token>

📦 Main API Modules
Authentication
POST /api/auth/register
POST /api/auth/login

Products
GET    /api/products
GET    /api/products/:id
POST   /api/products
PUT    /api/products/:id
DELETE /api/products/:id

Inventory
GET  /api/inventory
POST /api/inventory/stock-in
POST /api/inventory/stock-out
GET  /api/inventory/low-stock

Suppliers
GET    /api/suppliers
POST   /api/suppliers
PUT    /api/suppliers/:id
DELETE /api/suppliers/:id

Purchases
GET  /api/purchases
POST /api/purchases
GET  /api/purchases/:id
PUT  /api/purchases/:id

🔒 Role-Based Access Control
Example:

router.post(
    "/",
    authMiddleware,
    authorizeRoles("admin", "inventory_manager"),
    createProduct
);

Only users with the admin or inventory_manager role can create products.

🧪 Testing
Run tests using:

npm test

For coverage:

npm run test:coverage

🔐 Security
The project follows basic backend security practices:

Passwords are hashed using bcrypt.

JWT is used for authentication.

Protected routes require authentication.

Role-based authorization restricts access.

Environment variables store sensitive configuration.

.env is excluded from Git.

User input should be validated before database operations.

Database queries should be protected against injection.

Production deployments should use HTTPS.

📊 Inventory Workflow
Supplier
   │
   ▼
Purchase Order
   │
   ▼
Receive Products
   │
   ▼
Increase Stock
   │
   ▼
Inventory
   │
   ├── Stock Available
   │
   └── Low Stock Alert
           │
           ▼
      Reorder Product

🤖 AI-Augmented Development
AI tools can be used to assist development by:

Generating boilerplate code

Creating API endpoints

Generating test cases

Finding potential bugs

Improving documentation

Refactoring code

Reviewing security issues

Creating database queries

AI-generated code should always be reviewed and tested before being used in production.

🤝 Contributing
Fork the repository.

Create a new branch:

git checkout -b feature/new-feature

Make your changes.

Add tests.

Commit your changes:

git commit -m "feat: add inventory management"

Push the branch:

git push origin feature/new-feature

Create a Pull Request.

📄 License
This project is licensed under the MIT License.

👨‍💻 Author
Your Name

Product Inventory Management System
Built with Node.js, Express.js, and MongoDB.
