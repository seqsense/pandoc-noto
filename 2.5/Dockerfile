FROM ubuntu:xenial

RUN apt-get update -qq \
  && apt-get install --no-install-recommends -y \
    ca-certificates \
    etoolbox \
    lmodern \
    make \
    texlive-latex-recommended \
    texlive-xetex \
    unzip \
    wget \
  && apt-get clean && rm -rf /var/lib/apt/lists

RUN wget -q https://noto-website-2.storage.googleapis.com/pkgs/NotoSerifCJKjp-hinted.zip -O /tmp/NotoSerifCJKjp.zip \
  && mkdir -p $HOME/.fonts/NotoSerifCJKjp \
  && unzip /tmp/NotoSerifCJKjp.zip -d $HOME/.fonts/NotoSerifCJKjp \
  && rm /tmp/NotoSerifCJKjp.zip

RUN wget -q https://noto-website-2.storage.googleapis.com/pkgs/NotoSansCJKjp-hinted.zip -O /tmp/NotoSansCJKjp.zip \
  && mkdir -p $HOME/.fonts/NotoSansCJKjp \
  && unzip /tmp/NotoSansCJKjp.zip -d $HOME/.fonts/NotoSansCJKjp \
  && rm /tmp/NotoSansCJKjp.zip

ENV PANDOC_VERSION 2.5

RUN wget -q https://github.com/jgm/pandoc/releases/download/${PANDOC_VERSION}/pandoc-${PANDOC_VERSION}-linux.tar.gz -O /tmp/pandoc.tar.gz \
  && cd /tmp && tar xzf /tmp/pandoc.tar.gz \
  && ls -la /tmp/pandoc-${PANDOC_VERSION} \
  && cp -r /tmp/pandoc-${PANDOC_VERSION}/* /usr/ \
  && rm -rf /tmp/pandoc.tar.gz /tmp/pandoc-${PANDOC_VERSION}

WORKDIR /work
