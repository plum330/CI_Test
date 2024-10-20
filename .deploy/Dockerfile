FROM hub.class100.com/ops/golang:1.19

WORKDIR /app

COPY . .

ENV GO111MODULE on
ENV GOPROXY=https://goproxy.cvn,direct
RUN GOOS=linux CGO_ENABLED=1 \
  go build -ldflags="-s -w" -installsuffix cgo -o server main.go

ENV TZ=Asia/Shanghai
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

CMD ["./server"]
