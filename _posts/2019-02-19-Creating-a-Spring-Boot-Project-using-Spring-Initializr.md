今天用 Spring 官网提供的 [Spring Initializr](https://start.spring.io)来创建一个Spring项目。  
项目类型选择Maven Project，语言选择Java，Spring Boot版本默认当前最新发布版本。  
我们可以对Project Metadata进行自定义，另外还可以更具需要选择依赖，这里我们选择 web和Actuator。  
设置好后，点击 Generate Project 按钮，会下载一个Spring项目骨架。  
![image](http://ww1.sinaimg.cn/large/b6489cc0gy1g0b573yar6j21wo0oqq7j.jpg)

接着我们把项目导入到IDEA。  
导入到IDE后，发现项目报错：Cannot resolve symbom 'springframework'。如下：
![image](http://ww1.sinaimg.cn/large/b6489cc0gy1g0b4yuisztj219y0dgjtn.jpg)

首先想到的是新项目需要在Project Structure里面指定一下SDK，但是这种方式并没有解决问题。
![image](http://ww1.sinaimg.cn/large/b6489cc0gy1g0b5nufbjgj21ba0jmaew.jpg)

再打开pom，发现maven找不到相关的Spring包。  
这时候进入到maven ～/.m2 下面修改settings.xml  
把默认的镜像修改成下面这样，再次reimport maven project就好了。
```
<mirror>
    <id>nexus-aliyun</id>
    <mirrorOf>*</mirrorOf>
    <name>Nexus aliyun</name>
    <url>http://maven.aliyun.com/nexus/content/groups/public</url>
</mirror>
```
**最终效果如下：**
![image](http://ww1.sinaimg.cn/large/b6489cc0gy1g0b67f126nj222a194qf6.jpg)
