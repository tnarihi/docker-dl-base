FROM tnarihi/docker-python:cuda7.5

RUN apt-get install -y wget
RUN wget https://cmake.org/files/v3.1/cmake-3.1.3.tar.gz
RUN tar xvf cmake-3.1.3.tar.gz
RUN apt-get install -y cmake
ENV CMAKE_PATH /opt/cmake-3.1.3
RUN cd cmake-3.1.3 && mkdir build && cd build && cmake -D CMAKE_INSTALL_PREFIX=${CMAKE_PATH} .. && make && make install
ENV PATH $CMAKE_PATH/bin:${PATH}
RUN cd ../.. && rm -rf cmake-3.1.3
RUN apt-get install -y unzip
RUN pip install cython
RUN pip install pytest
RUN pip install pytest-rerunfailures
RUN apt-get install -y clang-format-3.4
RUN apt-get install -y git-core
RUN apt-get install -y doxygen \
    flex \
    bison
ENV DOXYGEN_PATH /opt/doxygen-latest
RUN git clone https://github.com/doxygen/doxygen.git && cd doxygen && mkdir build && cd build && cmake -DCMAKE_INSTALL_PREFIX=${DOXYGEN_PATH} .. && make install && cd ../../ && rm -rf doxygen
ENV PATH ${DOXYGEN_PATH}/bin:${PATH}
RUN apt-get install -y zsh
