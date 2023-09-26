Afin de pouvoir utiliser les différentes applications GeoServices de manière directe et transparente, il est nécessaire d'installer un serveur reverse proxy [NGINX](https://nginx.org), qui va s'occuper du mapping des URL sur les bons ports.

### Marche à suivre

1. Copier le [Dockerfile](https://gitlab.avasad.ch/geos/nginx-server/-/blob/main/ops/build/Dockerfile) dans le répertoire `/srv/geos/nginx-server` pour construire l'image `nginx-server` (ce fichier se trouve dans `/srv/geos/nginx-server/ops/build` car il est utilisé par les pipelines GitLab)

   ```shell
   cd /srv/geos/nginx-server
   cp ops/build/Dockerfile .
   docker build --network=host -t nginx-server .
   rm -f Dockerfile
   ```  

4. Créer le container Docker et déployer le serveur

   ```shell
   cd /srv/geos/nginx-server
   docker compose up -d
   ```
