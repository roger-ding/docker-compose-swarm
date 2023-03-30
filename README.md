# docker-compose-swarm
## Simple exercises demonstrating docker compose and docker swarm

---
### Docker Compose
```
$> docker compose up -d
```

Listing containers must show two containers running and the port mapping as below:
```
$> docker compose ps
NAME                       IMAGE                    COMMAND                  SERVICE             CREATED             STATUS              PORTS
docker-compose-backend-1   docker-compose-backend   "/code/bin/backend"      backend             2 seconds ago       Up 1 second
docker-compose-proxy-1     nginx                    "/docker-entrypoint.…"   proxy               2 seconds ago       Up 1 second         0.0.0.0:80->80/tcp
```

After the application starts, navigate to `http://localhost:80` in your web browser to confirm it is working

Stop and remove the containers
```
$> docker compose down
```

---
 
### Docker Swarm 

```
#Initilizes swarm environment 
$> docker swarm init 

#Check the current state of the swarm with container information
$> docker info 

#View information of nodes in the swarm 
$> docker node ls 

#Create a service with the CLI
$> docker service create --replicas {number of replicas} --name {service name} {image name} 

#Create a service with docker-compose file
$> docker stack deploy -c {docker-compose file name} {docker compose app name} 

#Scaling a service
$> docker service scale {service name}={number of replicas}

#Check for running services 
$> docker service ls

#View state of worker nodes
$> docker service ps {service name}

#Remove a service
$> docker service rm {service name}

#Leave Swarm 
$> docker swarm leave 

#Leave swarm forcefully 
$> docker swarm leave --force
```

