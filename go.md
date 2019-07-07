# Go 速查表

## TODO

- [ ] go 的代码块缩进需要使用2个空格

## Base

### Hello World

```go
package main

import "fmt"

func main() {
    fmt.Println("Hello")
}
```

## 变量和常量

### 变量定义

```go
// 先定义，再复制
var msg string
msg = "hello"
// 类型推导
msg := "hello" // 只能在函数中
// 抛弃无用的变量
data, _ := someFunc()
```

### 变量类型

```go
// string
str1 := "Hello"
str2 := `多行
数据`
// int
num1 := 3
// float64
num2 := 3.
// complex128
num3 := 3 + 4i
// byte (alias for unit8)
num4 := byte('a')
// array
arr1 := [...]int{1, 2, 3, 4, 5}
// slice
slice1 := []int{2, 3, 4}
slice2 := []byte("Hello")
// pointer
pointer1 := &slice1 // 获取变量的指针，即内存地址
slice1a := *pointer1 // 获取指针对应的变量的值
func func1(num1 *int) num1a *int { // 函数参数必须是指针，返回的也是指针
    a := *num1 + 10 // 获取 num1 指针对应的值
    return &a // 获取 a 的指针
}
// 类型转换
f1 := float64(num1) // int -> float64
u1 := uint(num1) // int -> uint
```

### 常量定义

```go
const Pi = 3.14
```

## 流程控制

### if ... else ...

```go
// 常规用法
if day == "sunday" || day == "saturday" {
    fmt.Println("rest")
} else if day == "monday" && isTired() {
    fmt.Println("groan")
} else {
    fmt.Println("work")
}
// if 中带语句
if _, err := someFunc(); err != nil {
    fmt.Println(err)
}
```

### for

```go
// 常规用法
for i := 0; i < 10; i++ {
    fmt.Println(i)
}
// for-range
for index, value := range entity {
    fmt.Println(index, value)
}
```

### switch

```go
switch day {
    case "monday":
    	fmt.Println("groan")
    case "saturday":
    	fallthrough
    case "sunday":
    	fmt.Println("rest")
	default:
    	fmt.Println("work")
}
```

## 函数

```go
func mod10(x int) int {
    retrun i1 % 10
}
// 匿名函数
x := 10
myFunc := func() bool {
    return x > 1000
}
// 多返回值
func getMessage() (string, string) {
    return "Hello", "World"
}
a, b := getMessage()
// 返回值可命名
func split(sum int) (x, y int) {
    x = sum * 4 / 9
    y = sum - x
    return
}
```

## 包

### 定义包

```go
// 定义当前包名为hello
package hello
```

### 导入

```go
// 单个包
import "fmt"
// 多个包
import (
	"fmt"
    "math/rand" // 一般以最后一个“/”后的名字作为包的引用名字
)
```

### 导入别名

```go
// 单个包导入别名
import r "math/rand"
// 多个包别名
import (
	r "math/rand"
    // ... 其他要导入的包
)
```

### 导出

```go
// 以大写字母开头的任何变量、方法等都会认为是可到处的
func Hello() {
}
```

## 并发

### 携程

```go
// 新建携程执行指定函数
go myFunc()
// 新建携程执行匿名函数
go func () {
}
```

### 管道

```go
// 创建管道
ch1 := make(chan string)
// 向管道中写入数据
ch1 <- msg1
// 从管道中读取数据
msg2 <- ch1
// 带缓冲的管道
ch2 := make(chan int, 2)
// 关闭管道
close(ch1)
// 遍历管道中的数据，直到管道停止
for i := range ch {
}
// 获取管道的数据，并返回管道是否关闭的状态
v, ok := <- ch1 // 如果 ok == false 则说明管道已经关闭了
```





