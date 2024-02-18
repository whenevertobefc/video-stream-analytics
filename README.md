# Video Stream Analytics

Below is the architecture diagram for Video Stream Analytics application. Read the article at [InfoQ](https://www.infoq.com/articles/video-stream-analytics-opencv)

![Video Stream Analytics Architecture](https://github.com/baghelamit/video-stream-analytics/blob/master/architecture.png)

Video Stream Analytics application includes following two applications. Please check Readme of these two applications for more details.

- Video Stream Collector
- Video Stream Processor



## 步骤

### 安装jdk8

自行安装

### 安装maven

自行安装

### 安装opencv

不同平台有不同的安装方式，选择具体的操作系统进行安装

得到如下的目录，最终在启动java进程添加如下jvm参数`-Djava.library.path=/opt/homebrew/Cellar/opencv/4.9.0_3/share/java/opencv4`

![image-20240218171155193](https://cdn.jsdelivr.net/gh/thend03/mdPic/picGo/202402181711274.png)

### 安装kafka

参照如下文档安装kafka: https://kafka.apache.org/quickstart

启动好kafka之后，创建topic，topic在video-stream-collector的配置文件里

### 安装spark

在下载页下载spark: https://spark.apache.org/downloads.html

选择具体版本然后下载，解压之后启动spark

![image-20240218171631906](https://cdn.jsdelivr.net/gh/thend03/mdPic/picGo/202402181716937.png)



执行start-master.sh就启动好了

![image-20240218171816993](https://cdn.jsdelivr.net/gh/thend03/mdPic/picGo/202402181718021.png)

### 启动processsor

Video-stream-processor模块是处理kafka的流数据，经过spark处理，输出图片到文件目录

启动需要添加jvm参数: -Djava.library.path=/opt/homebrew/Cellar/opencv/4.9.0_3/share/java/opencv4

路径自行替换

stream-processor.properties里有输出路径，按照实际情况修改

### 启动collector

collector模块是收集视频流数据，本例是使用离线的demo运行

启动需要添加jvm参数: -Djava.library.path=/opt/homebrew/Cellar/opencv/4.9.0_3/share/java/opencv4

实际路径自行替换



另外还需要修改stream-collector.properties里的视频文件，里面是相对路径，需要修改为绝对路径



启动之后就可以在/tmp/processed-data/路径下查看视频提取出的图片了
