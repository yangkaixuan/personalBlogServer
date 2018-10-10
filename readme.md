# 个人博客网站
##简介
######1.服务器用的是express框架，express框架为基于Node.js平台的极简web开发框架。详情请访问http://www.expressjs.com.cn/
######2.服务器管理模块用的是forever网站，它是一个简单的命令式nodejs的守护进程，能够启动，停止，重启App应用。GitHub地址为https://github.com/foreverjs/forever

## 调试使用：
```
npm i  安装所有依赖
```
```
npm install forever -g 如果没有安装forever的话请先安装forever
```
```
cd 到项目目录下

npm start 运行启动项目

npm stop 停止运行项目
```
	  
## forever 常用命令

	// 1. 简单的启动
	forever start app.js
	// 2. 指定forever信息输出文件，当然，默认它会放到~/.forever/forever.log
	forever start -l forever.log app.js
	
	// 3. 指定app.js中的日志信息和错误日志输出文件，
	//  -o 就是console.log输出的信息，-e 就是console.error输出的信息
	forever start -o out.log -e err.log app.js
	
	// 4. 追加日志，forever默认是不能覆盖上次的启动日志，
	//  所以如果第二次启动不加-a，则会不让运行
	forever start -l forever.log -a app.js
	
	// 5. 监听当前文件夹下的所有文件改动
	forever start -w app.js
	
	// 1. 监听当前文件夹下的所有文件改动（不太建议这样）
	forever start -w app.js
	
	显示所有运行的服务
	复制代码 代码如下:
	forever list
	
	停止操作
	复制代码 代码如下:
	// 1. 停止所有运行的node App
	forever stopall
	// 2. 停止其中一个node App
	forever stop app.js
	// 当然还可以这样
	// forever list 找到对应的id，然后：
	forever stop [id]

	重启操作
	
	重启操作跟停止操作保持一致。
	
	复制代码 代码如下:
	// 1. 启动所有
	forever restartall
	开发和线上建议配置
	
	复制代码 代码如下:
	
	// 开发环境下
	NODE_ENV=development forever start -l forever.log -e err.log -a app.js
	// 线上环境下
	NODE_ENV=production forever start -l ~/.forever/forever.log -e ~/.forever/err.log -w -a app.js
	
	上面加上NODE_ENV为了让app.js辨认当前是什么环境用的。不加它可能就不知道哦？
	一些注意点
	
	有可能你需要使用unix下的crontab（定时任务）
	这个时候需要注意配置好环境变量。
	
	复制代码 代码如下:
	SHELL=/bin/sh
	PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
## 托管静态文件
	在public目录下可托管文件例如在 public 文件夹下加入icon.png 文件 通过 www.yangkaiuxan.com/icon.png 就可访问
