## Nginx가 제공해줄 build 파일들을 생성하는 단계
FROM node:16-alpine as builder

WORKDIR /app

COPY ./package.json ./

RUN npm install

COPY . .

RUN npm run build

## Nginx가 제공해줄 build 파일들을 제공하는 단계
FROM nginx
EXPOSE 3000

## default.conf 파일을 nginx 컨테이너 안에 있는 default.conf 파일에 덮어씌움
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/build  /usr/share/nginx/html

