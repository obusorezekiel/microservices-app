### 🔥 **Week 4: Advanced Kubernetes Deployment with GitOps** 🔥  

**Task Overview:**  
This week, you’ll work on deploying a multi-component microservices application to Kubernetes using **GitOps principles** and automating workflows across **three repositories**:  

1. **Infra Repo:** Manage cloud infrastructure provisioning and configuration with **Terraform** and **Ansible**.  
2. **Application Repo:** Handle microservices source code, Dockerfiles, and CI pipelines for Docker image management.  
3. **K8 Manifests Repo:** Store Kubernetes manifests for the microservices application (excluding ArgoCD manifests, which are managed by Ansible).  

📌 **Steps to Complete the Task:**  

### 1. **Repository Setup**  
Create the following repositories:  
- **Infra Repo:** Terraform and Ansible configurations for Kubernetes cluster and tool installations.  
- **Application Repo:** Fork and clone the **current repository** (the one you are reading the instructions from). This repository will contains the microservices source code, Dockerfiles, and CI pipelines for Docker image management.  
- **K8 Manifests Repo:** Kubernetes manifests for deploying the microservices application.  

---

### 2. **Infrastructure Provisioning (Infra Repo)**  
#### Tools: **Terraform**, **Ansible**  
- Use **Terraform** to provision a Kubernetes cluster on your chosen cloud provider.  
- Use **Terraform** to trigger **Ansible** to perform the following tasks, with each task implemented as an **Ansible role**:  
  1. **ArgoCD Installation**:  
     - Install ArgoCD on the cluster using Helm.  
  2. **ArgoCD Application Setup**:  
     - Create and manage ArgoCD application manifests to deploy the microservices application from the **Application Repo**.  
  3. **Logging Stack Setup**:  
     - Deploy **EFK (Elasticsearch, Fluentd, Kibana)** or **ELK (Elasticsearch, Logstash, Kibana)** using Helm.  
  4. **Monitoring Stack Setup**:  
     - Install the **Kube-Prometheus Stack** using Helm for metrics and monitoring.  

---

### 3. **Application Deployment (Application Repo)**  
#### Tools: **GitHub Actions**, **Trivy**, **Docker Hub**  
- **Fork and Clone the Current Repo**:  
  - Fork and clone the **current repository** (the one you’re reading the instructions from) into your own GitHub account. This will be the **Application Repo**.  

- **Pre-build Docker Images**:  
  - Each microservice already has its Dockerfile.  
  - Build Docker images for all services and push them to a **public Docker Hub repository**.  

- **CI Pipeline for Docker Images**:  
  - Create a **CI pipeline for each microservice** in the **Application Repo**.  
  - Each CI pipeline should:  
    1. Build the Docker image.  
    2. Scan the image for vulnerabilities using **Trivy**.  
    3. Push the image to the **Docker Hub repository**.  
  - Trigger conditions for CI pipelines:  
    - Manually.  
    - When changes are made to the specific folder containing the Dockerfile for a given microservice.  

---

### 4. **Kubernetes Manifests Management (K8 Manifests Repo)**  
- Store all Kubernetes manifests for deploying the microservices application, such as:  
  - Deployments.  
  - Services.  
  - ConfigMaps.  
  - PersistentVolumes, etc.  
- Ensure these manifests reference the pre-built Docker images from **Docker Hub**.  
- Exclude **ArgoCD manifests**, as they are managed by Ansible in the **Infra Repo**.  

---

📋 **Requirements:**  

1. **Infrastructure Management:**  
   - Use Terraform to provision the Kubernetes cluster.  
   - Use Ansible roles for installing and configuring:  
     - ArgoCD (via Helm).  
     - EFK/ELK stack (via Helm).  
     - Kube-Prometheus stack (via Helm).  
     - ArgoCD application manifests (for deploying the microservices app).  

2. **Application Management:**  
   - CI pipelines in the **Application Repo** must include:  
     - Docker image build.  
     - Trivy vulnerability scan.  
     - Docker Hub push.  
   - Docker images must be pre-built and uploaded to Docker Hub for all microservices.  

3. **Kubernetes Deployment:**  
   - Microservices application is deployed via ArgoCD, pulling manifests from the **K8 Manifests Repo**.  

4. **Logging and Monitoring:**  
   - EFK/ELK stack and Kube-Prometheus stack are set up and functional.  

5. **Triggering Conditions:**  
   - Ansible tasks are triggered by Terraform.  
   - CI pipelines are triggered manually or when changes are detected in a microservice's folder in the **Application Repo**.  

---

✅ **Acceptance Criteria:**  

1. **Repositories Created and Used:**  
   - Infra Repo (Terraform and Ansible configurations).  
   - Application Repo (microservices source code, Dockerfiles, and CI pipelines).  
   - K8 Manifests Repo (Kubernetes manifests for microservices).  

2. **Infrastructure Provisioning:**  
   - Kubernetes cluster is provisioned with Terraform.  
   - Ansible successfully configures the cluster with ArgoCD, EFK/ELK, and Kube-Prometheus stack.  

3. **Functional Deployment:**  
   - Microservices application is successfully deployed to Kubernetes using ArgoCD.  
   - Logging and monitoring systems are operational.  

4. **Docker Images Pre-Built and Published:**  
   - Docker images for all microservices are available on Docker Hub.  

5. **Pipeline Validations:**  
   - CI pipelines are functional for each microservice and meet the stated trigger conditions.  

---

📝 **Submission Instructions:**  
Submit the following by **11:59 PM WAT, Monday, 23rd December 2024**:  
1. Links to the **three GitHub repositories**.  
2. Screenshots of:  
   - Kubernetes cluster.  
   - Logs and monitoring dashboards (EFK/ELK and Kube-Prometheus).  
   - CI pipelines (Trivy scan results and Docker Hub upload success).  
3. A detailed blog post documenting your process, including the **architectural diagram** 
