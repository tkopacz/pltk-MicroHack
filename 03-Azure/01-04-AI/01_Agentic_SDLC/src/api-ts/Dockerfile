FROM node:24-alpine AS builder

WORKDIR /app
COPY api-ts/package*.json ./
RUN npm install
COPY api-ts/ .
RUN npm run build

FROM node:24-alpine
WORKDIR /app
COPY api-ts/package*.json ./
RUN npm install --omit=dev
COPY --from=builder /app/dist ./dist
COPY database /database

EXPOSE 3000
CMD ["npm", "start"]
