# Installing Docker
All labs in this repository are run using Docker containers. To download Docker, refer to their documentation pages: https://docs.docker.com/get-docker/.

# Cloning the repository
To clone the repository locally use the following command:
```
git lfs clone https://github.com/PacktPublishing/Software-Security-Testing.git
```

If you do not have Git installed, refer to their installation pages: https://github.com/git-guides/install-git. Make sure to install git-lfs to ensure all files are properly cloned: https://docs.github.com/en/repositories/working-with-files/managing-large-files/installing-git-large-file-storage.

# Running the lab using the run.sh and docker-compose files

### Loading Docker images
Each lab is compressed in a tar image that can be easily imported as a Docker image. Note the following example:
```
cd "LDAP Injection Lab"
docker load -i ldap.tar
```

In Linux based operating systems, this process is automated via the load_images.sh script. First make sure the file is an executable by running the following command:
```
chmod u+x load_images.sh
```
Then, run it to import all tar files as Docker images:
```
./load_images.sh
```

### Using docker-compose
When all tar files are imported, all Docker labs can be started at once using the following command:
```
docker-compose up -d
```

# Building labs with Docker
To build each lab without using the tar files provided, follow these steps:

### Build the Docker images
```
docker build -t common_attacs Common\ Web\ Vulnerabilities\ Lab/Common_attacks/
docker build -t session_puzzling Session\ Puzzling\ Lab/SessionPuzzle/
docker build -t cors Cross\ Origin\ Resource\ Sharing\ Lab/CORS/
docker build -t ldap LDAP\ Injection\ Lab/Ldap-injection/
docker build -t url_redirect URL\ Redirect\ Lab/Url-redirection/
```

### Start the Docker containers
```
docker run --name common_attacks --hostname common_attacks -p 80:80 common_attacs
docker run --name session_puzzle --hostname session_puzzle -p 5000:5000 session_puzzling
docker run --name ldap_injection --hostname ldap_injection -p 5002:5002 ldap
docker run --name cors_attack --hostname cors_attack -p 5003:5003 cors
docker run --name redirect --hostname redirect -p 5004:5004 url_redirect
```
### Stop the Docker containers
To stop the running containers, if using docker-compose, run the following command:
```
docker-compose down
```
To stop each container individually use the following command:
```
docker stop container_name
docker rm container_name
```

# Note
These labs were build to demonstrate security issues. Please make sure to stop the labs once you have completed course exercises.
