# Container Images

This repository is used to host and keep track of my container based images.


## CI: Build and publish Docker image (Docker Hub)

- **Workflow path:** `.github/workflows/docker-publish.yml` — builds the image under `images/base` and pushes to Docker Hub.
- **Registry:** Docker Hub — the workflow requires `DOCKERHUB_USERNAME` and `DOCKERHUB_TOKEN` to be set in repository secrets.

### Secrets to configure (GitHub repository settings -> Secrets)
- **`DOCKERHUB_USERNAME`**: your Docker Hub username.
- **`DOCKERHUB_TOKEN`**: a Docker Hub access token or password.

### Image names produced
- Docker Hub: `<dockerhub-username>/images-base:latest` and `<dockerhub-username>/images-base:<commit-sha>`

### Test locally
Build the image locally from the repository root:

```bash
docker build -t images-base:local -f images/base/Dockerfile ./images/base

# (optional) push to Docker Hub:
docker login -u <username>
docker tag images-base:local <username>/images-base:local
docker push <username>/images-base:local
```

Add the two required secrets in the repository's Secrets to allow the CI to push to Docker Hub.
