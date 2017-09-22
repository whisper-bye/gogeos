FROM ubuntu:16.04

RUN mkdir /build

RUN apt-get update && \
    apt-get install -y --fix-missing --no-install-recommends \
    wget build-essential mingw-w64

RUN wget http://download.osgeo.org/geos/geos-3.3.8.tar.bz2

RUN tar xvfj geos-3.3.8.tar.bz2 && \
    cd geos-3.3.8 && \
    ./configure --host=x86_64-w64-mingw32 --target=x86_64-w64-mingw32 --build=x86_64-pc-linux-gnu --prefix=/build && \
    make -j$(nproc) && \
    make install

WORKDIR /workspace

CMD cp -r /build /workspace
