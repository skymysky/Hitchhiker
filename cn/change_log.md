#### 0.6 2017-12-18

**Features:**

* \#45 重写压力测试，支持现有所有新特性，比如ES6, 自定义的js包
* 重新整理请求流程，参考流程图：[workflow](https://raw.githubusercontent.com/brookshi/images/master/Hitchhiker/script/reuqest_wf.png) 
* 环境变量在所有脚本内都可用
* \#47 如果response是图片的话就直接显示图片，而不是图片内容

**Bugs:**

* \#62 global function 里的内容在切换模块后会消失
* \#59 schedule里的请求返回是图片时，会造成JSON.parse失败，导致异常，改了图片只保存链接，不保存内容
* \#55 浏览器里压力测试的websocket有时会失败，加了重试
* schedule的定时跑的记录会有1分钟左右的误差
* 改请求的method时name会被重置


#### 0.5 2017-11-28

**Features:**

* \#41 Script 增加属性request来得到请求的信息，增加方法setRequest(request)来对请求进行修改。
* \#41 在Collection下增加Common Pre Request Script，这里可以对Collection下的所有request起作用。
* \#42 增加配置 inviteMemberDirectly 来设置邀请Project成员时是否需要通过邮件，true即直接加到Project里，默认为true。
* \#43 使用gitbook重新组织了文档： https://brookshi.gitbooks.io/hitchhiker/content/cn/introduction.html
* \#44 在Collection下增加option: Request Follow Redirect，决定这个Collection下的请求是否需要在状态码为3xx时继续跳转，默认为false。
* \#51 在Collection下增加option: Request Strict SSL，决定这个Collection下的请求是否验证SSL证书是否合法，默认为false。


#### 0.4.2 2017-11-18

**Bugs:**

* \#50 压力测试异常，错误使用setInterval


#### 0.4.1 2017-11-15

**Bugs:**

* \#40 post数据大于1M时出现异常: Payload Too Large


#### 0.4 2017-11-13

![](https://raw.githubusercontent.com/brookshi/images/master/Hitchhiker/pre_request_script.PNG)

**Features:**

* 增加 pre request script。
* \#29 项目文件夹系统，支持上传js或数据文件到文件夹并可以在脚本里使用它们。
* \#22 schedule支持以小时或分钟为单位。
* \#34 支持自定义邮件发送接口。
* \#24 开放schedule的run now接口以便其他程序调用。

**Bugs:**

* \#24 schedule的顺序执行无效
* sync有时会覆盖用户已经更改的数据
* sync时环境变量编辑对应框里的内容会被清掉


#### 0.3 2017-10-30

![](https://raw.githubusercontent.com/brookshi/images/master/Hitchhiker/sync.gif)

**Features:**
* 支持数据自动同步更新

**Bugs:**
* 修正url不支持中文


#### 0.2 2017-10-15

![](https://raw.githubusercontent.com/brookshi/images/master/Hitchhiker/stresstest.gif)

**Features:**

* 支持压力测试

* 支持在源码部署时改端口

**Bugs:**

* 修正Schedule跑空Collection时的异常


#### 0.1.3 2017-09-24

![](https://raw.githubusercontent.com/brookshi/images/master/Hitchhiker/parameters.gif)

**Features:**
* 参数化请求，可以使用随机组合的`ManytoMany`或者一对一组合的`OnetoOne`。 请求通常有很多参数，比如query string, body等，这些参数可能会有不止一个值，每个都要覆盖的话需要写很多request，比如一个request有三个可变的参数，每个参数又有3个值，随机组合下来会有`3*3*3=27个request`，这很麻烦，其实它们之前只是一点不同，现在可以使用参数来帮你做这个事，只需要把可变的参数写在parameter里面，系统会自动构建出request。

* 做schedule对比数据前可以先处理返回的response，再用处理后的数据进行比对，在test里使用 $export$(data) 来导出需要比对的数据。

* \#13 请求的默认headers，这些header可以在根目录下的appconfig.json里配置，默认定义的是这些：
``` json
"defaultHeaders": [
    "Accept:*/*",
    "User-Agent:Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/60.0.3112.113 Safari/537.36",
    "Cache-Control:no-cache"
]
```

**Bugs:**

* 没有处理test返回undefined的情况，改为返回失败

* 如果request不包含cookie且本地也没有cookie时发了空的cookie header，改为不发cookie header

* Save As request时原request会受到影响


#### 0.1.2 2017-09-09

**Features:**

* 添加清除本地Cache功能

* request的header提示及自动完成

* 可以收藏常用的request header，方便下次使用

* 可以在Project里定义tests的全局函数，方便其下的Request直接使用

* 略微调整UI


#### 0.1.1 2017-08-26

**Features:**

* Request历史记录

* 成员可以添加Localhost映射

* 在Collection/Folder的菜单里创建Request

* Schedule可以选择是否要对某个Request做match

* Schedule的结果在Request前面加上Folder

* 免登录试用

**Bugs:**

* 复制Request后源Request的headers有时会丢失

* Schedule编辑对话框应该只能选择当前Collection的环境

* 跑空Schedule会出错

* 选择了Project的话Folder不能展开


#### 0.1.0 2017-07-24