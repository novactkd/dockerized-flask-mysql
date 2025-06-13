
# Dockerized Flask App with MySQL - DevOps Demo Project

This project is a simple two-tier Flask web application connected to a MySQL database, fully containerized using Docker. It demonstrates key DevOps practices such as containerization, Docker Compose, environment configuration, CI/CD pipeline integration with Jenkins, and Kubernetes manifests for deployment.


## Project Overview

- **Frontend:** Flask app to submit and display messages.
- **Backend:** MySQL database storing messages.
- **Containerization:** Dockerfiles and Docker Compose setup.
- **CI/CD:** Jenkins pipeline defined in `Jenkinsfile`.
- **Kubernetes:** Manifests provided in `eks-manifests` and `k8s` folders for deploying the app on Kubernetes clusters.

This project serves as a practical demo to help beginners understand Docker, CI/CD, and Kubernetes in a real-world scenario.

---

## Prerequisites

Make sure the following are installed on your system:

- [Docker](https://docs.docker.com/get-docker/)
- [Docker Compose](https://docs.docker.com/compose/install/)
- [Git](https://git-scm.com/) (optional, for cloning the repo)
- [Jenkins](https://www.jenkins.io/) (optional, for CI/CD pipeline demo)
- [kubectl](https://kubernetes.io/docs/tasks/tools/) (optional, for Kubernetes deployment demo)

---

## Setup Instructions

1. **Clone the repository:**

   
   git clone https://github.com/Aiman-ui/dockerized-flask-mysql.git
   cd dockerized-flask-mysql
````

2. **Create a `.env` file in the root directory with your MySQL configuration:**

   ```bash
   touch .env
   ```

   Add the following environment variables in `.env`:

   ```
   MYSQL_HOST=mysql
   MYSQL_USER=your_mysql_user
   MYSQL_PASSWORD=your_mysql_password
   MYSQL_DB=your_database_name
   ```

3. **Build and start the containers using Docker Compose:**

   ```bash
   docker-compose up --build
   ```

4. **Access the Flask app:**

   * Open your browser at [http://localhost](http://localhost) to see the frontend UI.
   * The Flask backend API runs at [http://localhost:5000](http://localhost:5000).

5. **Create the `messages` table in MySQL:**

   Use any MySQL client or CLI and run:

   ```sql
   CREATE TABLE IF NOT EXISTS messages (
       id INT AUTO_INCREMENT PRIMARY KEY,
       message TEXT
   );
   ```

---

## Project Structure

```
├── Dockerfile
├── Dockerfile-multistage
├── Jenkinsfile
├── Makefile
├── README.md
├── app.py
├── docker-compose.yml
├── eks-manifests/         # Kubernetes manifests for EKS deployment
├── k8s/                  # Kubernetes manifests for local cluster deployment
├── message.sql           # SQL script for creating tables
├── requirements.txt
└── templates/            # HTML templates for Flask app
```

---

## CI/CD with Jenkins

The `Jenkinsfile` defines a basic pipeline to:

* Build Docker images
* Run tests (if any)
* Push images to a Docker registry (configure accordingly)
* Deploy the app (customize for your environment)

To run the pipeline, set up a Jenkins server, connect it to this repo, and run the job.

---

## Kubernetes Deployment (Optional)

Kubernetes manifests are provided in the `eks-manifests` and `k8s` folders to deploy both the Flask app and MySQL on Kubernetes clusters.

* Use `kubectl apply -f <manifest>` to deploy resources.
* Adjust configurations based on your cluster setup.

---

## Cleanup

To stop and remove Docker containers:

```bash
docker-compose down
```

---

## Notes

* Replace all placeholder values (e.g., MySQL credentials) with your actual settings.
* This project is for demo and learning purposes; production setups require additional security and performance considerations.
* Validate and sanitize inputs properly in production to avoid security risks.
* Check Docker and Jenkins logs for troubleshooting.

```
```
