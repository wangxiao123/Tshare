###golang 系列之 package flag的使用

####简介
在golang中，通过flag包来进行命令行参数的解析和使用。

例如（flag doc 中）：

Define flags using flag.String(), Bool(), Int(), etc.

This declares an integer flag, -flagname, stored in the pointer ip, with type *int.
	
	import "flag"
	var ip = flag.Int("flagname", 1234, "help message for flagname")

注意： 这里的 ip 是 指针类型。

####注意事项
使用flag需要注意以下几点：

   * 在命令行中使用的flag一定要通过 flag.String() 或者 flag.Int()等函数来定义
   * 在定义之后，一定要使用 `flag.Parse()` 来进行解析。
   * 命令行参数的格式 可以有几下几种：
	   * -flag arg
	   * --flag arg
	   * -flag=arg
	   * --flag=arg

   * 另外：为了避免解析bool时的二义性，请用 = 方式来指定。

	
		import (
			"flag"
			"fmt"
		)
		
		func main() {
		
			var numberflag = flag.Bool("n", false, "number each line")
			var filename = flag.String("name", "test", "file name")
		
			flag.Parse()
		
			fmt.Printf("%v %v", *numberflag, *filename)
		
		}

#### Usage
在flag中，有一个匿名函数

	var Usage = func() {
		.....
	}

此函数当参数解析失败时就会调用，显示Usage。用户可以自定义。

flag 包可以解析很多参数 详情请猛戳[官方doc][1]






[1]:http://golang.org/pkg/flag/

