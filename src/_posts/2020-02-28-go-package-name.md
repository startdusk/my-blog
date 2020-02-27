---
category: 后端
tags:
  - Golang
date: 2020-02-28
title: Golang：包的小知识
---

<!-- more -->

## Golang：包的小知识

在 Go 语言中，代码组织的形式是用包来组织，那么，我们有如下项目的目录结构

```bash
─project
    ├───core
    │   └───core.go
    ├───main.go
```

一般地，建议包名和文件夹的名称保持一致，避免为使用者带来不必要的麻烦。</br>
如在 core.go 中的代码为：

```go
package core

func Run() {}
```

那么，这个包名就是 core ，我们在 main.go 的调用方式就为：

```go
package main

import "core"

func main() {
  core.Run()
}
```

但是，当我们定义的包名和文件夹名不一致时，如将 core.go 的代码修改为：

```go
package util

func Run() {}
```

此时，core.go 的包名变为了 util , 那么在 main.go 的调用也要相应的做改变：

```go
package main

import "core"

func main() {
  util.Run()
}
```

那么，可以发现，import 导入的只是路径，实际调用还是使用包名调用，但不推荐包名和文件夹名不一致。</br>

还有一种情况是，当一个文件夹下只能有一个包，如 core 文件夹下有多个文件时，不能使用多个包名，这点在 Go 语言中是不允许的
