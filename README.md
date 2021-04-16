# Citizen Science Portal Proxy/Load Balancer

## Why?

- HTTPS with Let's encrypt
- Proxy
- Automatically discover Docker stack containers (with labels)
- This can be used any DO droplet with Docker

## What for

This docker stack is a base for the Gulf Citizen Science portal server.
https://gulfcitizenscience.org

When correctly set up the "labels" section in docker-compose.yml for Docker Stack, Traefik automatically discovers containers and routes of subdirectories. Besides, Traefik redirects routes to https with Let's Encrypt. No restarting nor resetting a web server required. Traefik handles it

## Set up

0. Docker must be installed
1. Download this repo
2. Install this at a new server/droplet
   - \$ docker-compose up -d
   - containers: traefik2, redis, mysql, whoami, nginx_data, zipkin
   - install portainer and/or prometheus as needed
   - https://domain.name/datasets: it shows the contents of ./nginx_data
   - modify traefik.toml as needed (e.g. Host)

3. Check if installed properly (https://domain.name/dashboard/)
Treafik Dashboard
![Image of Traefik Dashboard](images/traefik22.png)

## Install Data Portal and Frontend (Home page)
1. Install backend service (https://github.com/GCOOS/CitizenScience_dataportal)
2. Install the project home page with Dash/Plotly charts (https://github.com/GCOOS/CitizenScience_web)

## Reference
https://docs.traefik.io/user-guides/docker-compose/acme-tls/

