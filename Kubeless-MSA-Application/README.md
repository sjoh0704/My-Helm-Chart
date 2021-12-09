# Kubeless-MSA-Application Helm Charts



For installation, the following conditions must be satisfied.
## Install Version
- k8s cluster: v1.21.2
- helm: v3.7.1
- kubeless: v1.0.6-dirty
- argocd: latest

<br/>

## Requirements
You must prepare AWS S3 storage and secret object in cluster like the following 
```
apiVersion: v1
data:
    REACT_APP_ACCESS_KEY: [AWS Access key]
    REACT_APP_ACCESS_SECRET_KEY: [AWS Access secret key]  
    REACT_APP_REGION: [AWS Region name]
    REACT_APP_BUCKET_NAME: [AWS S3 bucket name]
kind: Secret
metadata:
    creationTimestamp: null
    name: aws-bucket-secret

```

<br/>

## Git clone
```
git clone https://github.com/sjoh0704/Sseung-Helm-Chart.git
cd Sseung-Helm-Chart/
sudo cp -r model /my-model
helm install metric-server metric-server
helm install test1 root
```

<br/>

When you release this chart and sync, you can see the following in Argo Dashboard. 
![appofapps](https://user-images.githubusercontent.com/66519046/145418090-5099a9d5-85cf-4670-b33b-dbb8a621ab07.png)



<br/>


### Directory Structure

```
.
├── backend
│   ├── Chart.yaml
│   ├── templates
│   │   ├── configmap.yaml
│   │   ├── deployment.yaml
│   │   └── service.yaml
│   └── values.yaml
├── checkface
│   ├── Chart.yaml
│   ├── templates
│   │   ├── function.yaml
│   │   └── hpa.yaml
│   └── values.yaml
├── frontend
│   ├── Chart.yaml
│   ├── templates
│   │   ├── configmap.yaml
│   │   ├── deployment.yaml
│   │   ├── secret.yaml
│   │   └── service.yaml
│   └── values.yaml
├── kafka
│   ├── Chart.yaml
│   ├── templates
│   │   ├── kafka.yaml
│   │   └── trigger.yaml
│   └── values.yaml
├── metric-server
│   ├── Chart.yaml
│   ├── templates
│   │   └── no-tls-metric-server.yaml
│   └── values.yaml
├── model
│   ├── female
│   │   ├── female-model
│   │   │   ├── keras_model.h5
│   │   │   └── labels.txt
│   │   ├── keras_model.h5
│   │   └── labels.txt
│   └── male
│       ├── keras_model.h5
│       ├── labels.txt
│       └── male_model
│           ├── keras_model.h5
│           └── labels.txt
├── mongodb
│   ├── Chart.yaml
│   ├── templates
│   │   ├── deployment.yaml
│   │   └── service.yaml
│   └── values.yaml
├── producer
│   ├── Chart.yaml
│   ├── templates
│   │   ├── function.yaml
│   │   └── hpa.yaml
│   └── values.yaml
├── README.md
└── root
    ├── Chart.yaml
    ├── templates
    │   ├── backend.yaml
    │   ├── checkface.yaml
    │   ├── frontend.yaml
    │   ├── kafka.yaml
    │   ├── mongodb.yaml
    │   └── producer.yaml
    └── values.yaml

21 directories, 47 files
```