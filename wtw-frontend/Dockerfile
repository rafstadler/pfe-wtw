FROM node:13.6.0-alpine as build

WORKDIR /app
COPY . .

RUN npm install --silent
RUN npm install react-scripts -g --silent 
RUN npm run build 

FROM nginx:1.16.0-alpine

COPY nginx.conf /etc/nginx/conf.d/default.conf
COPY --from=build /app/build /usr/share/nginx/html

EXPOSE 80 
CMD ["nginx","-g","daemon off;"]