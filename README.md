# Student Management Website – AWS Serverless Architecture

## Overview
This project is a **serverless student management website** hosted on AWS.  
It leverages AWS managed services to provide scalability, security, and cost efficiency.

---

## Architecture Diagram
![AWS Architecture]

<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/4a8ef4fb-7e6b-4b9c-890b-852791a29f14" />


## Components

### 1. **Amazon API Gateway**
- Acts as the entry point for client requests.
- Handles HTTP endpoints for student management functionalities such as:
  - Adding a student
  - Updating student records
  - Fetching student information
- Provides secure API access via **IAM Roles** and authentication mechanisms.

### 2. **AWS Lambda**
- Serverless compute that processes incoming API requests.
- Contains the backend business logic for:
  - Data validation
  - CRUD operations
  - Generating responses for the frontend
- Scales automatically based on request volume.

### 3. **Amazon DynamoDB**
- NoSQL database storing student records.
- Provides:
  - Low-latency data access
  - High availability
  - Scalability for unpredictable traffic

**Example Table Schema:**
| Attribute Name | Data Type   | Description                       |
|----------------|-------------|-----------------------------------|
| `studentId`    | Number (PK) | Unique identifier for each student |
| `name`         | String      | Student's full name               |
| `email`        | String      | Contact email                     |
| `Major`        | String      | Enrollment date                   |

---

### 4. **Amazon S3**
- Stores static frontend assets (HTML, CSS, JS).
- Configured for static website hosting.

---

### 5. **IAM Roles**
- Enforce **least privilege** for each AWS service interaction.
- Examples:
  - API Gateway → Lambda execution role
  - Lambda → DynamoDB read/write role
  - Lambda → S3 access role

---

### 6. **Amazon CloudWatch**
- Monitors logs, performance metrics, and errors.
- Used for:
  - Debugging Lambda functions
  - Tracking API Gateway performance
  - Setting up alarms for unusual activity

---

## Data Flow

1. **Frontend Request** – A user accesses the student management website hosted in **Amazon S3**.
2. **API Call** – The website makes a request to **API Gateway**.
3. **Lambda Execution** – API Gateway triggers an **AWS Lambda** function.
4. **Database Operations** – Lambda reads/writes to **Amazon DynamoDB**.
5. **Logging & Monitoring** – **CloudWatch** collects logs and metrics.


---

## Deployment Instructions

### Prerequisites
- AWS Account
- AWS CLI installed and configured
- Python for Lambda development

### Steps
1. **Create S3 bucket** for hosting website assets.
2. **Deploy frontend** files to S3.
3. **Set up DynamoDB** table for student records.
4. **Create Lambda functions** for backend logic.
5. **Create API Gateway endpoints** to trigger Lambda functions.
6. **Assign IAM roles** with required permissions.
7. **Enable CloudWatch logging** for all services.
8. Test and verify end-to-end functionality.

---

## Benefits
- **Scalable** – Serverless architecture automatically adjusts to load.
- **Cost-effective** – Pay only for usage.
- **Highly Available** – AWS managed services handle redundancy.
- **Secure** – Fine-grained IAM permissions.
