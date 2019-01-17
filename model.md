@[TOC](模块组合-应用模型)
> 普通接口调用比较常见，比如像微信公众平台、第三方平台接口调用。脚本逻辑以及纯业务组合都是基于接口链式调用的基础上,接口链式是基于模块组合模型展开，第二部分详解。
# 1、普通接口调用
>普通接口调用（标准型）-》普通接口调用（类似微信开发）

> Api调用，通过用户的appid与appKey换取授权的accessToken，通过授权的accessToken调用接口换取对应的数据，可进入开发者中心->接口调用工具->接口测试。

下图所示： 
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190117140044965.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI0Mjk1,size_16,color_FFFFFF,t_70)
原理调用图：
   ![在这里插入图片描述](https://img-blog.csdnimg.cn/20190117140231284.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI0Mjk1,size_16,color_FFFFFF,t_70)
   这是现在市场上比较常见的调用方式，已经大大的减少了开发工作量。
# 2、接口链式调用（目前可测试）
>接口链式调用（普通型）-》返回调用链编号调用（传入执行数据）

>接口链式调用出现为了减少第三方应用的开发工作量，直接通过模块组合，减少了用户调用多次的工作量，同时减少了用户的错误率。

接口链式调用逻辑图：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190117141510633.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI0Mjk1,size_16,color_FFFFFF,t_70)
根据这个模型，数据调用模型（简单版）：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190117142124328.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI0Mjk1,size_16,color_FFFFFF,t_70)
在平台中的操作流程：
## 1）先创建一个应用，选择对应的模块以及模型
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190117150731127.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI0Mjk1,size_16,color_FFFFFF,t_70)

## 2）选择接口链式调用，进入下一步
选择对应的模块：		
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190117151038375.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI0Mjk1,size_16,color_FFFFFF,t_70)
点击下一步
			
## 3）选择对应的接口，可拖拉排序
>注意：这边目前逻辑上还没有完全控制，接口链式组合是以操作为基础，如果需要用到查询加上自己的判断那就是在逻辑脚本中插入。

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190117151304955.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI0Mjk1,size_16,color_FFFFFF,t_70)
## 4）创建应用
>点击完成创建应用
## 5）创建成功后会生成一个应用编号
创建成功后有个应用编号：
![在这里插入图片描述](https://img-blog.csdnimg.cn/2019011715180487.png)
应用编号用于监控、日志、排查问题的唯一标识
## 6）进入开发者中心->接口调试工具->应用测试
>选择对应的应用，输入appId(12345)，传入数据（测试数据：{"orderName":"12345678232139","payName":"31231231","integralName":"123123"}）
>
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190117170456637.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI0Mjk1,size_16,color_FFFFFF,t_70)
点击测试：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190117145659244.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI0Mjk1,size_16,color_FFFFFF,t_70)
点击查看详情：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190117145810404.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI0Mjk1,size_16,color_FFFFFF,t_70)
requestDataFieldMap/resultDataFieldMap：这两个字段是请求数据的严格格式，现在默认为所有字段都通过检查，当有条件时，请求数据将严格筛选和检查，防止恶意数据。

在私有库中，可查看系统日志
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190117150041473.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI0Mjk1,size_16,color_FFFFFF,t_70)
点击查看（所有的请求记录都在上边）：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190117150151605.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI0Mjk1,size_16,color_FFFFFF,t_70)
## 7）查看数据情况
   >模块中心->模块详情
   
   点击模块
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190117165234885.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI0Mjk1,size_16,color_FFFFFF,t_70)   ![在这里插入图片描述](https://img-blog.csdnimg.cn/20190117165158497.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI0Mjk1,size_16,color_FFFFFF,t_70)
# 3、脚本逻辑调用
>脚本逻辑调用（进阶型）-》控制中间数据流转逻辑（可以回调通知外部应用）（市场产品：无）

>Route默认有路由规则，但是可以通过脚本来控制逻辑包括请求、数据流转，回调通知等（例如：
>{“step”:2,“notice”:“http：//URL/PATH”,”type”:”SUCCESS/ERROR/ALL”}）
就是路由第二步骤的时候将信息数据回调一份给url为“http：//URL/PATH”的地址，可以是成功消息、失败消息也可以是所消息。脚本语句有很多种，目前分为数据通知、重定向、数据清洗标准、回滚逻辑等。

# 4、纯业务组合型
>纯业务组合型（顶级型）-》通过脚本语句对多个模块逻辑直接调用，无需额外开发应用（市场产品：无）

>前面不管是接口链还是脚本逻辑，都处于第三方开发应用层面，纯业务组合型比较特殊，无需第三方开发的应用，但是有特殊的要求。
   标准：
1、	业务模块对应业务前端
        每个业务逻辑对应前端页面，在同一个环境里，用户openID与appid确定唯一性。这样子就实现业务插拔性。选择业务前端模块，就决定了服务端。以页面的按钮跳转确定业务逻辑。

所有的模块之间业务独立，唯一萃取这块与业务有关系，但是都是唯一性。为模块可插拔灵活提供了强大的支持。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190117154831633.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI0Mjk1,size_16,color_FFFFFF,t_70)
# 模块中心（概念，目前不能测试）
## 1）初始化模块
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190117153639591.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI0Mjk1,size_16,color_FFFFFF,t_70)
>输入模块名称、应用组、仓库地址以及代码版本
## 2）创建模块
![在这里插入图片描述](https://img-blog.csdnimg.cn/2019011715383371.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI0Mjk1,size_16,color_FFFFFF,t_70)
构建成功：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190117154023314.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM4NzI0Mjk1,size_16,color_FFFFFF,t_70)
进入测试容器环境，如果测试成功表示可以创建部署

