# Hello World Kubernetes

## A very simple .NET 5 demo

### Run from source

- `dotnet run`
- Open a browser to `http://localhost:5000`

### Build into a container using [Cloud Native Buildpacks](https://buildpacks.io)

- Install the [pack CLI](https://buildpacks.io/docs/tools/pack/)
- Run `pack build hello-world-k8s-dotnet --builder paketobuildpacks/builder:full`

### Run using Docker

- `docker run --interactive --tty --env PORT=8080 --publish 8080:8080 hello-world-k8s-dotnet`
- Open a browser to `http://localhost:8080`

### Run in Kubernetes

- To use your own image, you'll need to push it to an image registry and update the image location in the `deploy.yaml` file.
- `kubectl apply -f deploy.yaml`
- The `deploy.yaml` file creates a deployment with a service of type LoadBalancer. To access the application, open your browser to the EXTERNAL-IP shown when you run `kubectl get service hello-world-k8s-dotnet`.

Tested with .NET SDK 5.0.103, pack 0.17, and TKGm on AWS.
