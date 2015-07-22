## 前言
```
此版本修改自官方版skynet，改动部分如下：
1、sproto修改，添加了real（双精度浮点数double）的支持，以及variant类型（可以是real/int/string/bool）的支持
2、windows下不支持epoll，故采用event-select网络模型模拟epoll来保证最小改动skynet源码的情况下，实现网络通讯
3、windows平台下没有pipe兼容的接口，采用了socket api来模拟这一机制
4、控制台输入，hack修改了read函数来模拟读取fd 0(stdin)
```

## 编译
```
windows：
使用visual studio 2013直接打开build/vs2013/skynet.sln即可，目前暂时只支持这一个版本的编译器

linux/macos：
官方版一样
```

## 运行
```
windows：
1、工作目录设置为skynet.exe所在目录，默认为 $(ProjectDir)..\..\
2、命令参数设置为config文件的相对路径，如 examples/config

linux/macos：
和官方版一样
```

## Build

For windows, open build/vs2013/skynet.sln and build all
You can use vs ide to debugging skynet

```
## Difference between offical skynet
1.sproto support real(double)/variant(real/int/string) field type
2.used event-select to simulate epoll
3.use socket api to simulate pipe()
4.hack read fd(0) for console input
```

For linux, install autoconf first for jemalloc

```
git clone https://github.com/cloudwu/skynet.git
cd skynet
make 'PLATFORM'  # PLATFORM can be linux, macosx, freebsd now
```

Or you can :

```
export PLAT=linux
make
```

For freeBSD , use gmake instead of make .

## Test

Run these in different console

```
./skynet examples/config	# Launch first skynet node  (Gate server) and a skynet-master (see config for standalone option)
./3rd/lua/lua examples/client.lua 	# Launch a client, and try to input hello.
```

## About Lua

Skynet now use a modify version of lua 5.3.1 (http://www.lua.org/ftp/lua-5.3.1.tar.gz) .

For detail : http://lua-users.org/lists/lua-l/2014-03/msg00489.html

You can also use the other official Lua version , edit the makefile by yourself .

## How To (in Chinese)

* Read Wiki https://github.com/cloudwu/skynet/wiki
* The FAQ in wiki https://github.com/cloudwu/skynet/wiki/FAQ
