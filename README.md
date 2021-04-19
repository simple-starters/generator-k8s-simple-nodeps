# Simple generator for Kubernetes resources
A simple K8s generator, does not have any dependencies

This generator creates a Kubernetes Service and Deployment Resource to deploy a Spring Boot application. 

## Building and deploying the application

This generator relies on using the new `buildpack` support added in Spring Boot version 2.3 to create a container image.

If you are using Minikube you should configure your terminal to use the same Docker environment:

```bash
eval $(minikube docker-env)
```

**Step 1:** Build the project and create the container image:

```
./mvnw -DskipTests clean package spring-boot:build-image
```

**Step 2:** Deploy the app to Kubernetes

```
kubectl apply -f kubernetes/app
```

Use `kubectl get all` to verify that the resources created.

Accessing the application's endpoint varies based on the type of Kubernetes cluster you are using.  For example, if minikube is being used, look for the endpoint to access using the command `minikube service list`. For othetr Kubernetes clusters, you can use port-forwarding to access the service. Run `kubectl port-forward service/<name-of-service> 8080:80` to forward the service port to `localhost:8080`.

The README.md file from the code repository for the appliation should include a few `curl` commands to exercise the application.

# Generator Information

This generator creates the Kubernetes `service` and `deployment` resources files to deploy a Spring Boot application using `kubectl`

To use the generator you will need to install the following command line tool:

* [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/)



