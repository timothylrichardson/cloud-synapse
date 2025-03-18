## Cloud Synapse - Setup Guide

### Prerequisites
Ensure you have the following installed before proceeding:

- **Docker** (https://docs.docker.com/get-docker/)
- **Kubernetes (kubectl & minikube or a cluster)** (https://kubernetes.io/docs/setup/)
- **Helm** (https://helm.sh/docs/intro/install/)
- **AWS CLI** (if deploying to AWS) (https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html)

### Local Setup

1. **Clone the repository**
   ```sh
   git clone https://github.com/your-org/cloud-synapse.git
   cd cloud-synapse
   ```

2. **Build and run the Docker container**
   ```sh
   docker build -t cloud-synapse .
   docker run -p 8080:8080 cloud-synapse
   ```

3. **Verify the service is running**
   ```sh
   curl http://localhost:8080/health
   ```

### Kubernetes Deployment

1. **Start Minikube (if using local cluster)**
   ```sh
   minikube start
   ```

2. **Deploy to Kubernetes**
   ```sh
   kubectl apply -f k8s/
   ```

3. **Verify deployment**
   ```sh
   kubectl get pods
   kubectl get services
   ```

### AWS Deployment (Optional)

1. **Authenticate AWS CLI**
   ```sh
   aws configure
   ```

2. **Deploy using Helm (if applicable)**
   ```sh
   helm upgrade --install cloud-synapse helm/cloud-synapse -n cloud-synapse
   ```

3. **Monitor the deployment**
   ```sh
   kubectl get pods -n cloud-synapse
   ```

---
For troubleshooting, refer to the [docs](docs/README.md) or reach out to the maintainers.
