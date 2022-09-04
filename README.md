# Fiber Prometheus

Middleware for go fiber v2

## Installation

```bash
go get github.com/somprasongd/fiber-prometheus
```

## Examples

```go
package main

import (
  "github.com/gofiber/fiber/v2"
  fiberprometheus "github.com/somprasongd/fiber-prometheus"
)

func main() {
  app := fiber.New()

  p8sMiddleware := fiberprometheus.NewMiddleware("fiber", "http", "/metrics")
  p8sMiddleware.Register(app)

  app.Get("/", func(c *fiber.Ctx) error {
    return c.Send([]byte("Hello, Go World!"))
  })

  app.Get("/testurl", func(c *fiber.Ctx) error {
    return c.Send([]byte("this is testurl."))
  })

  app.Get("hello/:name", func(c *fiber.Ctx) error {
    return c.Send([]byte("Hello " + c.Params("name")))
  })

  app.Listen(":7000")
}

```
