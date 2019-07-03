# imooc_sparksql_project

### 项目简介

使用 SparkSQL 对imooc网站的用户行为日志数据进行清洗和处理，得到所要的结果，将其存储进数据库，并进行可视化展示。

#### 原始数据
```
183.162.52.7 - - [10/Nov/2016:00:01:02 +0800] "POST /api3/getadv HTTP/1.1" 200 813 "www.imooc.com" "-" cid=0&timestamp=1478707261865&uid=2871142&marking=androidbanner&secrect=a6e8e14701ffe9f6063934780d9e2e6d&token=f51e97d1cb1a9caac669ea8acc162b96 "mukewang/5.0.0 (Android 5.1.1; Xiaomi Redmi 3 Build/LMY47V),Network 2G/3G" "-" 10.100.134.244:80 200 0.027 0.027
```
- 原始数据内容包括：
	- 访问的系统属性： 操作系统、浏览器信息等；
	- 访问特征：点击的url、从哪个url跳转过来的(referer)、页面停留时间等；
	- 访问信息：session_id、访问IP（据此可得知访问城市）、访问时间等。

#### 需求
1. 统计最受欢迎课程的 Top N 访问次数
2. 按地市（根据IP）统计最受欢迎的 Top N 访问次数
3. 按流量统计最受欢迎的 Top N 课程
4. ......

---
### 项目流程

#### 1.数据清洗

原始数据：
```
183.162.52.7 - - [10/Nov/2016:00:01:02 +0800] "POST /api3/getadv HTTP/1.1" 200 813 "www.imooc.com" "-" cid=0&timestamp=1478707261865&uid=2871142&marking=androidbanner&secrect=a6e8e14701ffe9f6063934780d9e2e6d&token=f51e97d1cb1a9caac669ea8acc162b96 "mukewang/5.0.0 (Android 5.1.1; Xiaomi Redmi 3 Build/LMY47V),Network 2G/3G" "-" 10.100.134.244:80 200 0.027 0.027
```

1.1 初步清洗：
| Date | URL | Traffic| IP |
|:--:|||
|2017-05-11 14:09:14 |	http://www.imooc.com/video/4500	| 304 |218.75.35.226 |

1.2 进一步清洗：
| URL | Type | TypeId| Traffic | IP | City | Time |Date|
|:--:|||||||
|http://www.imooc.com/video/4500   |video  |4500 |304    |218.75.35.226  |浙江省 |2017-05-11 14:09:14|20170511|

其中 `IP地址 -> 城市` 使用了https://github.com/wzhe06/ipdatabase。

#### 2.数据处理



#### 3.数据存储



#### 4.数据可视化
