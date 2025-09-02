DevOps Project Phase 1 & 2

Prerequisites
Docker installed 

Building the Docker Image

Run the following command in the project folder to build the image and tag it "helloworld-app:1.0"

docker build -t helloworld-app:1.0 .

Running the Container
Run the following command:

docker run -p 8000:5000 helloworld-app:1.0

-p 8000:5000: speicifies the port used to access the app via your pc and the internal port used by docker. PCPORT:DOCKERPORT

the app should be available on http://localhost:8000 

Running with Kubernetes
This readme file assumes you are using minikube

1.Connect to the Minikube Docker Daemon
Since we are running this localy, we need to instruct Docker daemin to point to minkube's daemon:
minikube -p minikube docker-env | Invoke-Expression

2.Run docker build again:
docker build -t helloworld-app:1.0 .

3.Run the app.yaml file
in the project folder, run the command:

kubectl apply -f app.yaml

To access the deployed application in a Minikube cluster, run the following command to get the service URL:

minikube service helloworld-service

To stop the application, delete the resources:

kubectl delete -f app.yaml
