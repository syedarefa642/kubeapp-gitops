# 🚀 KubeApp - Kubernetes GitOps CI/CD Pipeline

A containerized web application deployed on **Kubernetes using Docker, Docker Hub, GitHub Actions, ArgoCD, K3s, and AWS EC2**.

The project demonstrates an end-to-end **GitOps-based CI/CD workflow** where code changes trigger a GitHub Actions pipeline, Docker images are built and pushed to Docker Hub, Kubernetes manifests are updated, and ArgoCD automatically deploys the changes to the Kubernetes cluster.

---

# 📌 Project Overview

This project implements an automated CI/CD and GitOps deployment pipeline for a frontend and backend application.

The workflow uses:

- GitHub for source code and GitOps repository
- GitHub Actions for CI automation
- Docker for containerization
- Docker Hub for image storage
- Kubernetes/K3s for container orchestration
- ArgoCD for continuous deployment
- AWS EC2 for hosting the Kubernetes cluster

---

# 🏗 Architecture

![KubeApp Architecture](images/architecture.png)

---

# 🔄 CI/CD Pipeline

The project follows a GitOps-based CI/CD workflow.

```text
Developer
   │
   ▼
GitHub Repository
   │
   │ Push to main
   ▼
GitHub Actions
   │
   ├── Build Frontend Docker Image
   ├── Push Image → Docker Hub
   └── Update Kubernetes manifest
             │
             ▼
      GitHub GitOps Repository
             │
             │ Argo CD watches repo
             ▼
           Argo CD
             │
             │ Automatic Sync
             ▼
       K3s Kubernetes Cluster
             │
       ┌─────┴─────┐
       ▼           ▼
   Frontend      Backend
       │
       ▼
    NodePort
       │
       ▼
   🌐 Website - (http://35.175.210.26:30080/status.html)
⚙️ CI Pipeline
GitHub Actions automatically performs the following tasks when changes are pushed to the main branch.
The CI pipeline performs:
Checkout Source Code
Login to Docker Hub
Build Frontend Docker Image
Push Docker Image
Generate Image Tag using Git Commit SHA
Update Kubernetes Deployment Manifest
Commit Updated Manifest
Push Changes to GitHub
<img width="1342" height="599" alt="Screenshot 2026-08-10 224720" src="https://github.com/user-attachments/assets/a6236249-24f6-43ca-ab39-73f0682983c9" />



