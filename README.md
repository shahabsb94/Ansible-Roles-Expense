#######################################################################################################################

                                            Expense App – Using Ansible Roles     

Introduction

The Expense Application is a full-stack web application built to manage and track personal or organizational expenses.
It is designed using a modern technology stack and deployed on AWS EC2 instances with complete automation using Ansible roles. This project represents an end-to-end DevOps workflow—covering development, configuration management, provisioning, deployment, and hosting.

Tech Stack & Tools Used

Node.js – Backend API service  | Nginx – Web server & reverse proxy | MySQL – Relational database for persistent storage

Infrastructure : 

AWS EC2 – Compute instances for Web, Backend, and MySQL - manually created on AWS console

AWS Security Groups – Controlled inbound/outbound rules

Amazon Linux 2 – Server OS

Automation & Configuration Management

Ansible

Used to configure servers

Install packages (Node.js, MySQL, Nginx)

Deploy application code

Manage services (nginx, backend service, mysqld)

Implement reusable roles for modularity

Version Control

Git & GitHub – Code management and collaboration


🏗️ Architecture Overview
                       ┌──────────────────┐
                       │      User        │
                       └────────┬─────────┘
                                │
                                ▼
                       ┌──────────────────┐
                       │      Nginx       │  (Frontend: Port 80)
                       └────────┬─────────┘
                                │ Reverse Proxy
                                ▼
                       ┌──────────────────┐
                       │    Node.js API   │ (Backend: Port 8080)
                       └────────┬─────────┘
                                │
                                ▼
                       ┌──────────────────┐
                       │      MySQL       │ (Port 3306)
                       └──────────────────┘

🛠️ Project Modules
1️⃣ Web Server (Nginx Role)

Installs & configures Nginx

Serves static frontend code

Sets up reverse proxy to backend

Ensures service is enabled & running

2️⃣ Backend Server (Node.js Role)

Installs Node.js & required packages

Downloads application artifact

Configures environment variables

Sets up a Systemd service for backend

Validates service health

3️⃣ Database Server (MySQL Role)

Installs MySQL 8.x

Configures root password securely

Creates required schema and users

Opens port 3306 only for backend server

Ensures MySQL starts on boot

🤖 Automation with Ansible Roles

Each layer is automated using separate roles for:
✔ MySQL
✔ Backend
✔ Frontend (Nginx)
✔ Common dependencies

This ensures reusability and clean separation of concerns.

📂 Folder Structure Example
Ansible-Roles-Expense/
│── inventory.ini
│── site.yaml
│── roles/
│   ├── mysql/
│   ├── backend/
│   ├── frontend/
│   └── common/

🔄 Deployment Workflow

Launch EC2 servers for:

MySQL

Backend

Frontend

Configure hosts in inventory.ini

Run the Ansible playbook:

ansible-playbook -i inventory.ini site.yaml


Ansible automatically:

Installs dependencies

Configures servers

Deploys app code

Starts services

Validates health

🎯 Objectives Achieved

Learned and implemented a multi-tier application deployment

Used configuration management with Ansible roles

Set up automated deployments and zero manual configuration

Strengthened understanding of Linux system administration

Practical experience with AWS EC2, Networking, and Service Management

📚 Future Enhancements

Add Terraform for automated infra provisioning

Configure Load Balancer + Auto Scaling

Implement CI/CD using GitHub Actions

Containerize using Docker

Move database to Amazon RDS


#######################################################################################################################