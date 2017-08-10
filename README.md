# echo-logrusmiddleware

![logrus middleware](/logrus.png)

An adapter (middleware) to make the Golang [Echo web
framework](https://github.com/labstack/echo) logging work with
[logrus](https://github.com/sirupsen/logrus), an excellent logging solution.

## Install

```
$ go get github.com/kpashka/echo-logrusmiddleware
```

## Usage

```go
package main

import (
	"github.com/sirupsen/logrus"
	"github.com/labstack/echo"
	"github.com/kpashka/echo-logrusmiddleware"
)

func main() {
	e := echo.New()

	// echo Logger interface friendly wrapper around logrus logger to use it
	// for default echo logger
	e.Logger = logrusmiddleware.Logger{logrus.StandardLogger()}
	e.Use(logrusmiddleware.Hook())

	// do the rest of your echo setup, routes, listen on server, etc..
}
```
