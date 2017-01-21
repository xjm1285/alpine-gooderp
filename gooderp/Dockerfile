FROM daocloud.io/xjm1285/alpine-postgres

ENV POSTGRES_USER good

COPY root /
RUN apk add --update --no-cache \
    build-base git curl \
    python python-dev py2-pip linux-headers \
    openldap-dev nodejs libxml2-dev libxslt-dev libjpeg-turbo-dev \
  && pip install virtualenv \
  && npm install -g less \
  && npm install -g less-plugin-clean-css \
  && virtualenv /env \
  && git clone http://github.com/osbzr/gooderp_addons /app/gooderp_addons \
  && git clone http://github.com/osbzr/base /app/base \
  && /env/bin/pip install -r /app/base/requirements.txt \
  && /env/bin/pip install simplejson \
  && adduser -D good \
  && chmod -R +x /etc/services.d
    
EXPOSE 8069

