FROM alpine:3.2

ENV CONSUL_VERSION 0.6.0
ENV CONSUL_SHA256 307fa26ae32cb8732aed2b3320ed8daf02c28b50d952cbaae8faf67c79f78847

# RUN apk --update add curl ca-certificates && \
#     curl -Ls https://circle-artifacts.com/gh/andyshinn/alpine-pkg-glibc/6/artifacts/0/home/ubuntu/alpine-pkg-glibc/packages/x86_64/glibc-2.21-r2.apk > /tmp/glibc-2.21-r2.apk && \
#     apk add --allow-untrusted /tmp/glibc-2.21-r2.apk && \
#     rm -rf /tmp/glibc-2.21-r2.apk /var/cache/apk/*

ADD https://releases.hashicorp.com/consul/0.6.0/consul_${CONSUL_VERSION}_linux_amd64.zip /tmp/consul.zip
RUN echo "${CONSUL_SHA256}  /tmp/consul.zip" > /tmp/consul.sha256 \
  && sha256sum -c /tmp/consul.sha256 \
  && cd /bin \
  && unzip /tmp/consul.zip \
  && chmod +x /bin/consul \
  && rm /tmp/consul.zip

ENTRYPOINT ["/bin/consul"]
