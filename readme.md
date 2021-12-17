
### GENERAL

example of manifest files:
- pod : apache.yaml
- deployment : deployment.yaml

to run a manifest file

```
kubectl apply -f <filename>

example:

kubectl apply -f deployment.yaml
```

usefull command
```
    watch <command>

example:

    watch kubectl get pods
```
## PODS

    - pods are the basic building block and atomic units of scheduling in kuberneties, they can hold one or multiple containers, and everytime we start a container it will be inside a pod.
    - For scalability it is advised to have a single container in each pod.
    - it s commom to have 2 container running on a pod, a primary container that runs our app and a secondary container that periodically pulls from github and update files that our first container is serving for instance 

example file 

to run command on a pod

```
kubectl exec <podName> <command>
```

to run commands from inside a pod 

```
kubectl exec -it -- bash
```

we can send request to localhost:3000 and forwarding it to apache server that is running on apache pod on port 80 by using this command

```
kubectl port-forward <podName> <hostPORT>:<podPORT>

example:

kubectl port-forward apache 3000:80

```

## DEPLOYMENT

Deployment is a Kubernetes resource that has many great features :
- reschedule pods once they die.
- helps in scaling, and rollout to newer versions, and rollback from bad releases without having downtime.