## Python hello world app running in minikube and  
### This Solution is simple application written in python which will print 'Hello World' with hostname where it is running on.

### Step 1-
prerequisite for windows 10 Home edition

1. Install Minikube for creating Kubernetes cluster on local/your desktop
[https://minikube.sigs.k8s.io/docs/start/]
2. Make sure virtualisation is on your machine 
[https://stackoverflow.com/questions/49005791/how-to-check-if-intel-virtualization-is-enabled-without-going-to-bios-in-windows]
4. If virtualisation is not on please make it enabled refer this for windows 10 [https://mashtips.com/enable-virtualization-windows-10/]
5. Download kubectl [https://kubernetes.io/docs/tasks/tools/]
6. Place both minikube and kubectl in same folder for the ease.
7. once all Install successfully move to Step 2.

### Step 2-
1. Download the app.py program which will print the hello world with hostname.
2. Download the docker file for the dockerizing the application
3. downlaod the service.yaml 

1. Start minikube from command line or powershell by this 'minikube start --vm-driver=virtualbox' command.
  This will create the single cluster running your machine in oracle virtual box. [https://www.youtube.com/watch?v=E2pP1MOfo3g&t=225s]
  IF virtualisation is on and still there is issue starting the vm then please use 'minikube start --no-vtx-check' to start the minikube.
2. Run 'eval $(minikube docker-env)' command to set the docker env in your minikube cluster.(Use bash terminal from Vscode or others).

#### Running application as deployment 
1. open bash terminal and set environment for docker 'eval $(minikube docker-env)'
2. Now we have our cluster running we will see docker service by 'docker images' or 'docker ps -a' , this will list all the images which are present.
5. Build the docker conatiner for our hello world python app  'docker build -t pywebdemo .'
3. downlaod or create service.yaml file for deployment
4. create deployment 'kubectl create deployment pyapp --image=pywebdemo'
5. create deployement by 'kubectl apply -f service.yaml'.
6. check service by 'kubectl get services' and 'kubectl get nodes'
7. expose the service to host machine port 'kubectl expose deployment hello-python --type=LoadBalancer --port=4000'
8. check services by 'kubectl get services'.
9. run service in browser by 'minikube service hello-python' this will open the app in default browser.
10. access the service on localhost with 'kubectl port-forward service/hello-python 8080:4000'
11. Minikube and Kubernetes provide a dashboard to visualize the deployment use this 'minikube dashboard' to see deployments in the browser.

### Cleanup
1. kubectl delete service hello-python
2. kubectl delete deployement hello-python
3. minikube stop ot minikube delete

