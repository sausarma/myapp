# Documentation
This Readme will guide you on how to provision a minikube kubernetes cluster on windows machine and deploy the myapp application.

# Kuberetes Cluster Setup
minikube is used to provision the kubernetes cluster locally. Use the below official link for the steps to create a cluster.
https://minikube.sigs.k8s.io/docs/start/

# Deploying the application
Application is named as "myapp" and depployed in "myapp" namespace.
To create the namespace, run:
kubectl apply -f myapp_ns.yaml

Once namespace is created, create the application and ClusterIP service
kubectl apply -f myapp.yaml;kubectl apply -f myapp_svc.yaml

<img width="807" height="307" alt="image" src="https://github.com/user-attachments/assets/928f536d-45fe-4c02-882c-10f7d81a6dab" />


# Deploying the ingress controller
minikube provides an easy way to deploy k8's nginx ingress controller. Just run the below command on your minikube cluster and you're good to go
minikube addons enable ingress

You should see the ingress controller getting created as below:

<img width="928" height="108" alt="image" src="https://github.com/user-attachments/assets/02839d9c-a0c2-4aa4-b5e0-9db537552679" />

# Exposing the application to internet using Ingress
once the ingress controller is created, you can now create the ingress object to expose myapp application.
kubectl apply -f myapp_ingress.yaml
This will create a ingress object and by making appropriate changes in /etc/hosts file, we can access our application using myapp.com

<img width="616" height="88" alt="image" src="https://github.com/user-attachments/assets/7b818d03-16b1-47d6-8c73-f97213441865" />


If you are using a linux machine, you need to add the below entry in /etc/hosts file, or if you are using windows, you need to add the entry in "C:\Windows\System32\drivers\etc\hosts"

192.168.59.101      myapp.com

Please note that the above ingress IP will be different for you and you need to fetch it using the command as shown in the screenshot.


