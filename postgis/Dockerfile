FROM kartoza/postgis:13.0

RUN localedef -i ja_JP -c -f UTF-8 -A /usr/share/locale/locale.alias ja_JP.UTF-8

ENV LANG ja_JP.UTF-8
ENV PGROONGA_VERSION=2.2.9-1

RUN apt update && \
  apt upgrade -y && \
  apt install -y wget && \
  wget https://packages.groonga.org/debian/groonga-archive-keyring-latest-buster.deb && \
  apt install -y -V ./groonga-archive-keyring-latest-buster.deb && \
  apt update && \
  apt install -y \
    postgresql-13-pgdg-pgroonga=${PGROONGA_VERSION} \
    groonga-normalizer-mysql \
    groonga-tokenizer-mecab && \
  apt clean && \
  rm -rf /var/lib/apt/lists/*

COPY ./postgis/sql/* /docker-entrypoint-initdb.d/