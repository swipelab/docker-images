FROM ubuntu:22.04

LABEL org.opencontainers.image.source=https://github.com/swipelab/docker-images
USER root

ARG flutter_version

RUN set -o xtrace \
    && cd /opt \
    && apt-get update \
    && apt-get install -y sudo wget zip unzip git openssh-client curl bc software-properties-common build-essential ruby-full ruby-bundler libstdc++6 libpulse0 libglu1-mesa locales lcov libsqlite3-dev --no-install-recommends \
    && git config --global user.email "support@swipelab.co" \
    && git config --global user.name "Swipelab CI"



ENV FLUTTER_HOME=${HOME}/sdks/flutter \
    FLUTTER_VERSION=$flutter_version
ENV FLUTTER_ROOT=$FLUTTER_HOME

ENV PATH ${PATH}:${FLUTTER_HOME}/bin:${FLUTTER_HOME}/bin/cache/dart-sdk/bin

RUN git clone --depth 1 --branch ${FLUTTER_VERSION} https://github.com/flutter/flutter.git ${FLUTTER_HOME}

RUN yes | flutter doctor \
    && chown -R root:root ${FLUTTER_HOME}