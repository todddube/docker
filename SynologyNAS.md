# Synology NAS Install Scripts ReadMe

## install prowlarr

docker run -d --name=prowlarr \
-p 9696:9696 \
-e PUID=1026 \
-e PGID=100 \
-e TZ=America/New_York \
-v /volume1/docker/prowlarr:/config \
--restart always \
ghcr.io/linuxserver/prowlarr

## Install radarr
docker run -d --name=radarr \
-p 7878:7878 \
-e PUID=1026 \
-e PGID=100 \
-e TZ=America/New_York \
-v /volume1/docker/radarr:/config \
-v /volume1/docker/radarr:/movies \
-v /volume1/docker/radarr:/downloads \
--restart always \
ghcr.io/linuxserver/radarr

# install sonarr
docker run -d --name=sonarr \
-p 8989:8989 \
-e PUID=1026 \
-e PGID=100 \
-e TZ=America/New_York \
-v /volume1/docker/sonarr:/config \
--restart always \
ghcr.io/linuxserver/sonarr

# install qbittorrent
docker run -d --name=qbittorrent \
-p 6881:6881 \
-p 6881:6881/udp \
-p 9865:9865 \
-e WEBUI_PORT=9865 \
-e PUID=1026 \
-e PGID=100 \
-e TZ=America/New_York \
-v /volume1/docker/qbittorrent:/config \
-v /volume1/docker/qbittorrent/downloads:/downloads \
--restart always \
ghcr.io/linuxserver/qbittorrent

# updated 02/25/2025
# install portainer
docker run -d --name=portainer \
-p 8000:8000 \
-p 9000:9000 \
-v /var/run/docker.sock:/var/run/docker.sock \
-v /volume1/docker/portainer:/data \
--restart=always \
portainer/portainer-ce