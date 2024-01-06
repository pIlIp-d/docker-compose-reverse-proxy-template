# docker-compose reverse proxy template
a little template o deploy your website and other projects behind a nginx-proxy with [Let’s Encrypt](https://de.wikipedia.org/wiki/Let%E2%80%99s_Encrypt) certificates.

## Setup
1. start the reverseproxy.
```
cd reverseproxy
docker-compose up -d
```
2. adapt and start your images 
Adapt the example config to your needs so that some application is exported to port 80 / 433.
Now set the following environment variables within your docker-compose.yml
```
...
environment:
 - VIRTUAL_HOST=yourdomain.com
  ...
```
and optionally add these for https and a certificate
```
- VIRTUAL_PROTO=https
- LETSENCRYPT_HOST=test2.computer.local
```
after that you can start the application by running:
```
cd <your-project>
docker-compose up -d
```
Now the application is accessable unde the specified subdomain or domain.
