# A Docker image that has the Emscripten SDK installed to /opt/emsdk
# Use this image to compile C/C++ code to WASM.

FROM launcher.gcr.io/google/clang-debian9 AS build
RUN apt-get update && apt-get upgrade -y && apt-get install -y \
  git \
  python \
  nodejs \
  default-jre

RUN cd /opt \
  && git clone https://github.com/juj/emsdk.git

WORKDIR /opt/emsdk

# These versions were available and worked on my local desktop as of Aug 2 2018.
RUN ./emsdk install emscripten-1.38.6 node-8.9.1-64bit clang-e1.38.6-64bit

RUN ./emsdk activate emscripten-1.38.6 node-8.9.1-64bit clang-e1.38.6-64bit

RUN /bin/bash -c "source ./emsdk_env.sh"

ENV EMSDK=/opt/emsdk

RUN mkdir -p /OUT /SRC