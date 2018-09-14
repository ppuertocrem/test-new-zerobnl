FROM docker:18.06

# Python 3.6.6 ---- 
# https://github.com/frol/docker-alpine-python3/blob/master/Dockerfile

RUN apk add --no-cache python3 && \
    python3 -m ensurepip && \
    rm -r /usr/lib/python*/ensurepip && \
    pip3 install --upgrade pip setuptools && \
    apk add --no-cache py-zmq && \
	rm -r /root/.cache

# Jupyter
RUN pip install ipython jupyter==1.0.0

# ZerOBNL ---------

ADD . /app
WORKDIR /app
RUN pip install -r requirements.txt

# WorkDir ---------

WORKDIR /code

CMD ["jupyter", "notebook", "--ip=0.0.0.0", "--port=8888", "--allow-root"]