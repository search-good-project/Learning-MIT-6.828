# Lab01

<!-- TOC depthFrom:2 -->

- [Lab01](#lab01)
	- [Boot xv6](#boot-xv6)
	- [sleep](#sleep)
		- [添加用户程序的步骤](#%e6%b7%bb%e5%8a%a0%e7%94%a8%e6%88%b7%e7%a8%8b%e5%ba%8f%e7%9a%84%e6%ad%a5%e9%aa%a4)
		- [C 语言基础知识](#c-%e8%af%ad%e8%a8%80%e5%9f%ba%e7%a1%80%e7%9f%a5%e8%af%86)
	- [ping-pong](#ping-pong)
	- [primes](#primes)
	- [find](#find)

<!-- /TOC -->

## Boot xv6

再准备工具链的时候，已经安装好了 xv6。现在可以直接 `checkout util` 了。

在 `xv6-riscv` 目录中，

```shell
$ make
$ make qemu
$
```

可以进入到 `xv6` 系统中。

```shell
$ ls
.              1 1 1024
..             1 1 1024
README         2 2 1982
xargstest.sh   2 3 93
cat            2 4 22664
echo           2 5 21560
forktest       2 6 11856
grep           2 7 26040
init           2 8 22264
kill           2 9 21488
ln             2 10 21464
ls             2 11 24944
mkdir          2 12 21608
rm             2 13 21592
sh             2 14 40384
stressfs       2 15 22592
usertests      2 16 107584
wc             2 17 23824
zombie         2 18 20992
cow            2 19 28936
uthread        2 20 24624
call           2 21 21544
kalloctest     2 22 26392
bcachetest     2 23 27512
mounttest      2 24 33168
crashtest      2 25 22712
console        3 26 0
$
```

## sleep

### 添加用户程序的步骤

以添加 `sleep` 用户程序为例。

1. 在 `xv6\user` 目录中，添加 `sleep.c` 文件
1. 在 `xv6\Makefile` 文件中的 `UPROGS` 属性后，添加 `$U/_sleep\` 行。
1. 在命令行中的 `xv6` 目录下，运行 `make fs.img` 命令。

我再尝试以上步骤的时候，把 `echo.c` 的内容完整了复制到了 `sleep.c`。所以，现在的 `sleep` 可以 echo 了，哈哈。

### C 语言基础知识

```c
#include "kernel/types.h"
#include "user/user.h"
```

就已经导入了所需的函数了，比如 `atoi`，不用再 include 具体的 C 文件了。

```c
int main(int argc, char *argv[])
```

中，

- **argc**，是指传入参数的个数。
- **argv**，是传入参数的数组。

## ping-pong

- `parent` 发送 `ping`
- `child` 发送 `pong`

## primes

我自己做的程序始终有问题，所以照着 [sieve.pdf](sieve.pdf) 中的程序，抄了一遍。居然可以。

## find

解答这一题，需要了解 unix 文件系统的细节知识。
