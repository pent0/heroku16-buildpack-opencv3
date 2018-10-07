# Version: 0.0.1
FROM heroku/heroku:16-build

# INSTALL ALL
RUN apt-get update && apt-get install -y  \
    libpq-dev \
    build-essential \
    cmake \
    pkg-config \
    libjpeg8-dev \
    libtiff5-dev \
    libjasper-dev \
    libpng12-dev \
    libavcodec-dev \
    libavformat-dev \
    libswscale-dev \
    libv4l-dev \
    libxvidcore-dev \
    libx264-dev \
    libgtk-3-dev \
    libatlas-base-dev \
    gfortran \
    liblzo2-2 \
    libopencv-dev

# DOWNLOAD
ENV OPENCV_VER 3.2.0

ENV LD_LIBRARY_PATH /usr/local/lib

ENV HOME /root
WORKDIR $HOME

RUN mkdir .heroku \
    && mkdir .heroku/vendor \
    && cp -r /usr/local/bin .heroku/vendor/ \
    && cp -r /usr/local/include .heroku/vendor/ \
    && cp -r /usr/local/man .heroku/vendor/ \
    && cp -r /usr/local/share .heroku/vendor/ \
    && cp -r /usr/local/lib .heroku/vendor/ \
    && cp -r /usr/lib/lib* .heroku/vendor/lib/ \
    && cp -r /usr/lib/x86_64-linux-gnu/lib* .heroku/vendor/lib/

# Clean buildpack
RUN rm -rf .heroku/vendor/lib/python* \
    && rm .heroku/vendor/lib/libicudata* \
    && rm .heroku/vendor/lib/libLLVM*

RUN tar -czvf "heroku16-buildpack-opencv${OPENCV_VER}.tar.gz" .heroku

CMD ["true"]
