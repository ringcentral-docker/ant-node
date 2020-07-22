### STAGE 1: Build ###
FROM openjdk:8 as base


# install node
ENV NODE_VERSION 11
RUN apt-get install -y curl \
  && curl -sL https://deb.nodesource.com/setup_${NODE_VERSION}.x | bash - \
  && apt-get install -y nodejs \
  && curl -L https://www.npmjs.com/install.sh | sh

RUN npm install -g yarn \
  && npm install -g @google/clasp

#install ant
ENV ANT_VERSION 1.10.8
RUN cd && \
    wget -q http://www.us.apache.org/dist//ant/binaries/apache-ant-${ANT_VERSION}-bin.tar.gz && \
    tar -xzf apache-ant-${ANT_VERSION}-bin.tar.gz && \
    mv apache-ant-${ANT_VERSION} /opt/ant && \
    rm apache-ant-${ANT_VERSION}-bin.tar.gz
ENV ANT_HOME /opt/ant
ENV PATH ${PATH}:/opt/ant/bin

# Show version
RUN node --version \
    && npm version && ant -version && java -version && git --version
