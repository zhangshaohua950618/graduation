#毕业设计
###简要叙述
我的想法是能够针对某一关键词，例如“美国大选”、“中国春节联欢晚会”这些持续性的话题。首先从微博抓取博文以及评论，以博文作为事件进行聚类，提取摘要，根据评论进行事件的情感分析，最后以Web端做数据展示                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            
##1.任务规划
- [x] 对于关键字进行微博爬取
    - [x] 长微博的处理
    - [x] 微博时间的转义
    - [x] 定时爬虫部署到云端
- [ ] 分词
- [ ] 统计词频
- [ ] 摘要提取
- [ ] 事件聚类
- [ ] 情感分析
- [ ] Web端数据展示

##2.分词

###[概率语言模型的分词方法][4]
####主要内容：
根据贝叶斯公式，将一个字串切分成很多单词序列[w1,w2,w3...]这会产生很多种的切分方案记录为s1，s2..
根据已经训练好的模型(单词出现的概率，即w的概率)连乘取其中概率最大的
####思考：
这个方法的假设是**单词之间是上下文无关的**，但是这个显然不符合中文的语境，然而这却貌似是主流方法，jieba分词使用的就是这种方法




##3.聚类
###[大规模短文本的不完全聚类][1]

####主要内容：
文章的主要讲，一般的聚类算法,切割法或者层次法比如，K-Means对于网络用语和短文本效果异常的差
主要原因有两点：
    - 出现“长尾现象”，即孤立点过多，难以聚类
    - 网络用语的表达

####思考：
文章中提出的解决方法是通过**不完全聚类解决**，孤立点过多只要是因为对于博文没有限制，而我所做的研究是对于特定话题进行抓取，
应该没有这方面问题

###[一种高效的用于文本聚类的无监督特征选择算法][2]
####主要内容:
- 分类是指在指定了类的情况下（有监督），在特征空间向量下面计算指定的文本与类的特征距离
- 聚类是只在没有指定类的情况下（无监督）将相似的归为一类
- 分类有很多优秀的方法，如信息熵和和卡方统计但这都是基于已经知道类的情况下，无法运用于聚类
- 文章提出的主要思路是将**第一次聚类的结果作为“类信息”**，第二次再根据这个结果进行分类

###[]

###[层次聚类、K-means聚类][3]
####主要内容:
KNN对于中心的选定十分关键，对于同样的k不同的初始节点对于结果影响很大，对于K的选取，我是否
可以假设每次关键事件的产生都会引起舆论的爆炸，以产生波动比较大的博文作为类的中心，但是怎样评价“比较高”～要尝试一下


###[KNN与k-MEANS的区别][5]
####主要内容：
knn是有监督的分类算法，而k-means是聚类算法
knn选取最近的k的节点中相似度最大的大多数作为预测
K-means选取最近的节点作为预测
####思考：
我在高热度的微博中已经聚类（层次聚类）出结果，现在是使用分类算法还是聚类算法？


##4.技术






[1]: http://jcip.cipsc.org.cn/CN/article/downloadArticleFile.do?attachType=PDF&id=1441
[2]: http://crad.ict.ac.cn/CN/article/downloadArticleFile.do?attachType=PDF&id=810
[3]: http://www.dataguru.cn/article-3408-1.html
[4]: http://book.51cto.com/art/201106/269050.htm
[5]: http://www.tuicool.com/articles/qamYZv