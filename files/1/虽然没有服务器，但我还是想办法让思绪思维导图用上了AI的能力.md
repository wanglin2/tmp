# 一些不重要的过程

众所周知，现在`AI`无处不在，你很难找到一个没有接入`AI`的产品。

而我开源的项目：**思绪思维导图**（[https://github.com/wanglin2/mind-map](https://github.com/wanglin2/mind-map)），又是一个天然适合接入AI的产品品类，有着明显的应用场景，比如可以帮你生成整个思维导图，或者帮你发散某个分支，所以再不加上就显得有点不合群了。

但是问题来了，要接入`AI`，那么就需要调用大模型服务商的接口，而思绪的网页版托管在`Github`上，域名肯定和大模型接口的域名不一样，而浏览器因为安全问题是不允许跨域调用接口的，除非接口允许，这个除非的意思就是如果阿里云腾讯云字节云之类的厂商接口不支持的话，就去跟他们说帮我支持一下，听着好像也不难，所以大家都选择在自己的服务器上调用，网页再调自己的服务器，当然这样也更安全，毕竟一些秘钥啥的不能泄露。

但是不用说服务器了，我连域名都买不起，怎么办呢？

突然想到思绪还有个客户端版，而客户端恰巧是用`Electron`和`Node.js`做的。

`Node.js`：我很强，写接口，小意思。

所以我只要在客户端里用`Node.js`起个服务来转发就可以了。

说干就干，并且在`DeepSeek`的指导下，两天就完成了接口调用和转发的代码，如果用传统的百度，大概可能也许需要两周。 

所以现在如果用的是思绪网页版，需要先下载客户端并启动，才能使用AI的能力，如果使用的是客户端，那么直接用就行了。

当然，调用大模型的接口也是需要付费的，域名都买不起的我肯定无法免费提供，所以需要自己去注册和申请，不过思绪接入的是`火山方舟大模型`，他们提供了很多个不同的大模型供你使用，并且每个模型都提供了很多的免费额度，也够免费用很久了，用完了么就再换个手机再注册一下，薅羊毛嘛，总有办法的。

效果如下：

1.一键生成：

![image-20250224173806896](C:\Users\wanglin25\AppData\Roaming\Typora\typora-user-images\image-20250224173806896.png)

![image-20250224173831841](C:\Users\wanglin25\AppData\Roaming\Typora\typora-user-images\image-20250224173831841.png)

2.续写：

![image-20250224173916798](C:\Users\wanglin25\AppData\Roaming\Typora\typora-user-images\image-20250224173916798.png)

3.对话：

![image-20250224173946154](C:\Users\wanglin25\AppData\Roaming\Typora\typora-user-images\image-20250224173946154.png)

## 详细使用教程

### 1.下载思绪客户端

可以去以下两个地址下载最新的客户端：

百度云：[https://pan.baidu.com/s/1huasEbKsGNH2Af68dvWiOg?pwd=3bp3](https://pan.baidu.com/s/1huasEbKsGNH2Af68dvWiOg?pwd=3bp3)

Github：[https://github.com/wanglin2/mind-map/releases](https://github.com/wanglin2/mind-map/releases)

注意一定要下载**0.13.1**及以上的版本，安装完后可以打开软件的关于弹窗里确认一下：

![image-20250224174829646](C:\Users\wanglin25\AppData\Roaming\Typora\typora-user-images\image-20250224174829646.png)

> 本篇文章发布时客户端可能还没有更新，耐心等待即可~

然后可以打开编辑页面，或者直接打开在线版：[https://wanglin2.github.io/mind-map/#/](https://wanglin2.github.io/mind-map/#/)

然后点击顶部的【AI】按钮，会显示一个输入`key`和`接入点`的弹窗（下图）：

![image-20250225090826084](C:\Users\wanglin25\AppData\Roaming\Typora\typora-user-images\image-20250225090826084.png)

接下来就可以去获取这两个值了。

### 2.注册火山方舟大模型

打开火山方舟大模型网站：

[https://console.volcengine.com/ark](https://console.volcengine.com/ark)

注册或登录进入。

选择左侧菜单的【在线推理】，然后点击【创建推理接入点】（下图）：

![image-20250224175615028](C:\Users\wanglin25\AppData\Roaming\Typora\typora-user-images\image-20250224175615028.png)

【接入点名称】随便填，然后点击【添加模型】（下图）：

![image-20250224175749203](C:\Users\wanglin25\AppData\Roaming\Typora\typora-user-images\image-20250224175749203.png)

模型你也可以随便选择自己喜欢的，比如`DeepSeek`（下图）：

![image-20250224175840347](C:\Users\wanglin25\AppData\Roaming\Typora\typora-user-images\image-20250224175840347.png)

确定后再点击【确认接入】就完成了（下图）：

![image-20250224180004672](C:\Users\wanglin25\AppData\Roaming\Typora\typora-user-images\image-20250224180004672.png)

你可以再次点击左侧的【在线推理】菜单，应该就可以看见刚开通的接入点：

![image-20250225091105837](C:\Users\wanglin25\AppData\Roaming\Typora\typora-user-images\image-20250225091105837.png)

把名称下面的字符串复制一下，这就是`推理接入点`（下图）：

![image-20250225091123459](C:\Users\wanglin25\AppData\Roaming\Typora\typora-user-images\image-20250225091123459.png)

粘贴到刚刚打开的思绪思维导图的弹窗里（下图）：

![image-20250225091218201](C:\Users\wanglin25\AppData\Roaming\Typora\typora-user-images\image-20250225091218201.png)

接下来点击左侧的【API Key管理】菜单，再点击【创建API Key】（下图）：

![image-20250225091407970](C:\Users\wanglin25\AppData\Roaming\Typora\typora-user-images\image-20250225091407970.png)

点击【创建】后就可以复制刚刚生成的`Key`了（下图）：

![image-20250225091515234](C:\Users\wanglin25\AppData\Roaming\Typora\typora-user-images\image-20250225091515234.png)

![image-20250225091530385](C:\Users\wanglin25\AppData\Roaming\Typora\typora-user-images\image-20250225091530385.png)

然后粘贴到思绪上点击【确认】就完成了（下图）：

![image-20250225091623076](C:\Users\wanglin25\AppData\Roaming\Typora\typora-user-images\image-20250225091623076.png)

此时再次点击思绪顶部的【AI】按钮，就会显示输入主题自动生成的弹窗了：

![image-20250225091738406](C:\Users\wanglin25\AppData\Roaming\Typora\typora-user-images\image-20250225091738406.png)

也可以激活某个节点，点击鼠标右键，点击【AI续写】来发散某个分支：

![image-20250225091906664](C:\Users\wanglin25\AppData\Roaming\Typora\typora-user-images\image-20250225091906664.png)

最后，你也可以点击右侧的【AI】按钮来直接进行对话：

![image-20250225092133395](C:\Users\wanglin25\AppData\Roaming\Typora\typora-user-images\image-20250225092133395.png)

如果你想知道免费额度还剩多少，可以再次重复前面的【推理接入点】创建过程，再选择模型那一步可以看到某个模型还剩多少（下图）：

![image-20250225093240216](C:\Users\wanglin25\AppData\Roaming\Typora\typora-user-images\image-20250225093240216.png)

如果所剩不多了，那么你就换个模型再创建一下，同时更新一下`推理接入点`到思绪上就可以了。

以上就是所有内容，有问题的话欢迎评论区留言~

