FROM node:lts-alpine

ENV HOME="/app"

WORKDIR ${HOME}

RUN apk update && \
  apk upgrade && \
  npm install -g npm && \
  npm update -g && \
  npm cache clean --force && \
  apk add git && \
  apk add --no-cache curl && \
  curl -o- -L https://yarnpkg.com/install.sh | sh

ENV PATH $HOME/.yarn/bin:$HOME/.config/yarn/global/node_modules/.bin:$PATH

# ホットリロード
ENV CHOKIDAR_USEPOLLING=true

RUN yarn install && \
  yarn add yarn && \
  yarn upgrade --latest

ENV HOST 0.0.0.0
EXPOSE 3000

CMD ["/bin/sh"]