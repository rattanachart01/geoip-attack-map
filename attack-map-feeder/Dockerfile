FROM python:3.9.13-buster

WORKDIR /app

RUN apt-get -y update
RUN apt-get -y install unzip


COPY attack-map-feeder/* ./attack-map-feeder/
COPY requirements.txt ./

RUN pip3 install -U -r requirements.txt
RUN find .

WORKDIR /app/DataServerDB
COPY GeoLite2-City.mmdb.gz ./
RUN gunzip GeoLite2-City.mmdb.gz
RUN find .

ENV GEOIP_REDIS_HOST redis-master
ENV GEOIP_HQ_IP 8.8.8.8

WORKDIR /app/attack-map-feeder
ENTRYPOINT ["./start.bash"]