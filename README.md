# udagram_micro

This is the Udagram app implementation repo using microservices for feed and user backends. The repo also includes frontend and a configuration file for nginx that will be used as a reverse proxy for feed and user microservices.

These repo contains 4 images in total:
- turanmerter/udacity-restapi-feed
- turanmerter/udacity-restapi-user
- turanmerter/reverseproxy
- turanmerter/udacity-frontend

All the images can be created using this command: 
`docker-compose -f docker-compose-build.yaml build --parallel`

In order to use these images in a kubernetes environment, all the YAML files under k8s directory have to be used:
```
kubectl apply -f env-configmap.yaml
kubectl apply -f env-secret.yaml
kubectl apply -f aws-secret.yaml
kubectl apply -f reverseproxy-service.yaml
kubectl apply -f frontend-service.yaml
kubectl apply -f backend-user-service.yaml
kubectl apply -f backend-feed-service.yaml
kubectl apply -f reverseproxy-deployment.yaml
kubectl apply -f frontend-deployment.yaml
kubectl apply -f backend-user-deployment.yaml
kubectl apply -f backend-feed-deployment.yaml
```

Note: env-configmap.yaml, env-secret.yaml and aws-secret.yaml contain sensitive information and they have to be filled before running.
