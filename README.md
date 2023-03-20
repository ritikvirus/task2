# Domain Name Of The Server, Which Displays “Hello World”
[TASK-2_CLICK-HERE](https://ritikvirus.xyz)

# Docker hub link
[Docker-Repo](https://hub.docker.com/repository/docker/ritikvirus/task2/general)

# NGINX Route Blocks
```
server {
    server_name ritikvirus.xyz www.ritikvirus.xyz;
    listen 80;
    listen [::]:80;
    location / {
        proxy_set_header    Host $host;
        proxy_set_header    X-Real-IP $remote_addr;
        proxy_set_header    X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header    X-Forwarded-Proto $scheme;
        proxy_pass http://127.0.0.1:8080/;
    }
}
server {
    server_name ritikvirus.xyz www.ritikvirus.xyz;
    listen 443 ssl http2;
    listen [::]:443 ssl http2;
    ssl_certificate /etc/letsencrypt/live/ritikvirus.xyz/fullchain.pem;
    ssl_certificate_key /etc/letsencrypt/live/ritikvirus.xyz/privkey.pem;
    include /etc/letsencrypt/options-ssl-nginx.conf;
    ssl_dhparam /etc/letsencrypt/ssl-dhparams.pem;
    location / {
        proxy_set_header    Host $host;
        proxy_set_header    X-Real-IP $remote_addr;
        proxy_set_header    X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header    X-Forwarded-Proto $scheme;
        proxy_pass http://127.0.0.1:8080/;
    }
}
```
