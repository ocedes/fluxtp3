 # Create build stage based on buster image
FROM golang:1.22.3-alpine AS builder 
# Create working directory under /app
WORKDIR /app # Copy over all go config (go.mod, go.sum etc.)
COPY go.* ./
 # Install any required modules
RUN go mod download
 # Copy over Go source code
COPY *.go ./
 # Run the Go build and output binary under hello_go_http
RUN go build -o /hellogo main.go 
# Create a new release build stage
FROM alpine:latest 
# Set the working directory to the root directory path
WORKDIR /
 # Copy over the binary built from the previous stage
COPY --from=builder /hellogo /hellogo
EXPOSE 8080
ENTRYPOINT ["/hellogo"]

