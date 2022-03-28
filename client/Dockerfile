FROM node:16-alpine as builder

WORKDIR /app
COPY ./package.json /app/
RUN yarn install
COPY . .
RUN yarn build

FROM nginx
EXPOSE 3000
COPY ./nginix/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html
