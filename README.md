***Combines info from https://cloud.google.com/kubernetes-engine/docs/quickstarts/deploy-app-container-image and
https://github.com/knative/docs/tree/c85e40487b24923142fcf10fa96d1b7ec73b470d/code-samples/community/serving/helloworld-rust  
helloworld-rust example requires an update to the Rust Docker Image version (included in this code)  
Also requires a deployment.yaml file to be included and changes to be made to service.yaml as included here***

docker build -t simonholgate/helloworld-rust .
docker push simonholgate/helloworld-rust

***Assumes gcloud project has been created with apis enabled for kubernetes***  
gcloud container clusters create-auto helloworld-rust  --location us-central1
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml

***Get the external IP***  
kubectl get services

***Test***  
curl <EXTERNAL_IP>
