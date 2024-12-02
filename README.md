# Cosmocloud-Deploy

This Helm chart deploys a sample application stack with three services:
- **Backend**: Serves the application logic.
- **Frontend**: User interface.
- **Redis**: Caching layer.

## Deployment Structure

### Services
1. **Backend**
   - Service Type: ClusterIP
   - Port: 8000
2. **Frontend**
   - Service Type: NodePort
   - Port: 5175
   - NodePort: 31000
3. **Redis**
   - Service Type: ClusterIP
   - Port: 6379

### Environment Variables
- **Backend**:
  - `REDIS_URI`: `redis://redis-svc:6379`
- **Frontend**:
  - `BACKEND_URL`: `http://backend-svc:8000`

## Prerequisites
1. Kubernetes cluster.
2. Helm CLI installed.
3. Minikube (or any other K8s implementation tool).

## Installation
Run the following command to install the application and deploy it on kubernetes:
```bash
helm install testapp cosmocloud-deploy --atomic --timeout 30s
```

## Validation
- Ensure all pods are running:
```bash
kubectl get pods
```
- Check services:
```bash
kubectl get services
```

## Running on Browser 
Run the following command to access the application on the browser:
```bash
minikube service <frontend-service>
```

Use the link or IP/Port information to access the application on the browser.