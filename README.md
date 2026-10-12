# Flask App in Docker on AWS EC2

A simple Flask application packaged in a Docker image and deployed on an AWS EC2 Ubuntu instance.

## Files

- sanapp.py: the Flask app
- requirements.txt: Python dependencies
- Dockerfile: builds the image

## Run locally

    docker build -t san-flask-app .
    docker run -d -p 5000:5000 san-flask-app

Open http://localhost:5000

## Deploy on AWS EC2

1. Launch an Ubuntu EC2 instance
2. In the security group, allow SSH (22) and the app port (5000)
3. Connect over SSH and install Docker: `sudo apt update && sudo apt install docker.io -y`
4. Clone this repository: `git clone https://github.com/sanjaybalane/docker-flask-app.git`
5. Build and run the container with the commands above
6. Open http://<EC2-PUBLIC-IP>:5000

## Limitations and next steps

- Port 5000 is open to the internet. Restricting the source IP or putting the app behind a reverse proxy would reduce exposure.
- The container runs as root and uses an older Python base image. Next step: a maintained slim image and a non-root user.
- Deployment is manual. Next step: automate it with a CI/CD pipeline.
