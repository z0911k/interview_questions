## 移动研究院

### 1、BERT和GPT的区别？它们主要用于什么任务？
Bert和GPT都是深度学习中的NLP模型，它们都使用了Transformer的结构。区别主要在于Bert是encoder部分，是一种自编码模型。而GPT是一种自回归模型。

Bert在训练的时候会随机屏蔽（mask）一些词，然后根据上下文的信息来预测被屏蔽的词。这样模型可以学习到整个文本的语义信息，适合于下游的任务，如：问答，文本分类、实体识别等。

GPT的自回归模型，在训练的时候会利用前面的词来预测下一个词，这样模型学习到文本的生成规律，适合于文本生成、摘要、对话等任务。

### 2、梯度消失的原因？有什么方法可以缓解？
梯度消失的原因是因为在梯度反向传播的过程中，梯度函数有一个累乘项，如果这个累乘项的值小于1，随着层数的增加，梯度会越来越小，最终接近于0.导致网络的权重无法有效的更新。

解决方式：

（1）使用激活函数，如ReLU系列，避免出现过多小于1的值

（2）增加BN层。使输入分布稳定，避免梯度值过大过小

（3）使用残差链接，使梯度直接从后面的层传递到前面，减少累乘

（4）使用门控循环单元（GRU），LSTM，循环神经网络中保持长期的信息流动

### 3、正则化的作用？L1正则化和L2正则化的区别？
正则化是在损失函数中加入一个惩罚函数，用来限制模型的复杂度，防止过拟合。

L1正则化是模型参数的绝对值作为惩罚项，使参数更稀疏，即许多参数为0，从而达到特征选择的效果

L2正则化是模型参数的平方和作为惩罚项，它可以使模型的参数变得平滑，即许多参数的值接近0，从而减少模型的波动


### 4、transformer轻量化的方式？如何减轻其计算复杂度？
Transformer轻量化的方式有以下几种：

在模块级别可以使用低质分解、稀疏注意力、局部注意力等方法来减少注意力机制的计算量

在模型级别，可以使用深度可分卷机、深度可分自注意力、Lite Transformer等方方法来减少模型的参数和计算复杂度

在训练的级别，可以使用知识蒸馏、量化、剪纸等方法，来压缩模型大小，提高模型效率


### 5、GBDT、XGBoost、随机森林的区别？

GBDT，XGBoost和随机森林的区别主要有以下几点：

GBDT和XGBoost都是基于提升树（Boosting Tree）的算法，而随机森林是基于装袋树（Bagging Tree）的算法。

boost是一种串行的结构，每一棵树都是基于前面所有树的残差学习，而装袋树是一种并行的结构，每一棵树都是独立地从样本中抽取数据进行训练。

GBDT和XGBoost都是基于梯度提升（Gradient Boosting）的方法，而随机森林是基于自助法（Bootstrap）的方法。梯度提升是一种利用损失函数的负梯度作为残差的近似值，来优化模型的方法，而自助法是一种有放回地从样本中抽取数据的方法。

XGBoost在GBDT的基础上进行了改进和优化，主要有以下几个方面：

        XGBoost在目标函数中加入了正则项，用于控制模型的复杂度，防止过拟合；
  
        XGBoost先从顶到底建立所有可以建立的子树，再从底到顶反向进行剪枝，这样不容易陷入局部最优解；
  
        XGBoost支持并行计算，可以利用多核CPU和GPU加速训练过程；
   
        XGBoost支持自定义损失函数和评估指标，可以适应不同的问题场景；
  
        XGBoost支持缺失值处理，可以自动学习缺失值的最优分割点。

### 6、SVM多分类的方式？
SVM实现多分类的方式主要有两种：

一对一（One-vs-One）：对于K个类别，构造K(K-1)/2个二类分类器，每个分类器只对一对类别进行划分。最后根据投票或者其他规则确定最终的类别。

一对多（One-vs-Rest）：对于K个类别，构造K个二类分类器，每个分类器只对一个类别和其他所有类别进行划分。最后根据置信度或者其他规则确定最终的类别。

### 7、怎么判断一个函数是凸函数？
一阶导数是增函数，二介导数>=0

### 8、残差连接的作用是什么？

残差链接可以降低模型复杂度以减少过拟合：残差链接可以使模型更容易学到简单的映射，而不是在后面的层中学习复杂的非线性变换。

残差链接可以缓解梯度消失或爆炸的问题：残差链接可以使梯度更容易地从后面的层传递到前面的层，从而保持梯度的稳定性。

残差链接可以提高模型的表达能力：残差链接可以使模型更容易地捕捉到数据中的细微变化，从而提高模型的泛化能力。


## OPPO研究院

### Bert和word2vec的区别是什么？

Word2vec生成的是上下文无关的嵌入，也就是说每个单词只有一个向量表示。一旦训练好，词向量是不变的，只需要用key去索引就行了。
然而Bert模型生成的向量，根据不同上下文的不同是不同的，也可以说是动态的，这也是Bert能够更好地捕捉单词在不同上下文中的语义信息的原因。

### 遗传算法的流程？

遗传算法是一种启发式搜索算法，它通过模拟自然选择的过程来解决优化问题。通常的步骤如下：

（1）初始化：随机生成一组候选解决方案的种群

（2）计算适应度函数

（3）选择，从当前种群中选择适应度较高的个体

（4）交叉：对选定的个体进行交叉操作，生成新的种群

（5）变异：对新一代种群进行变异

（6）重复（2）（3）（4）（5）直到达到最大的迭代次数，或满足停止条件。

### Transformer和LSTM、RNN相比的区别，优势是什么？

RNN、LSTM是定向模型，也就是说它们是按照顺序从左到右理解每一个输入。而Transformer和Bert是一种非定向模型，它们能够更好的处理长距离依赖。并且Transformer的训练效率高，可并行化处理。


### Coding：快速排序、编辑距离、相交链表

## 腾讯

### transformer和transformerXL的区别？还有什么结构支持输出长文本

### Simhsh的的原理是什么？

simhash的算法具体分为5个步骤：分词、hash、加权、合并、降维，具体过程如下：

1.分词

给定一段语句或者一段文本，进行分词，得到有效的特征向量，然后为每一个特征向量设置一个5个级别（1—5）权值。例如给定一段语句：“生活本没有路，走的人多了就成了路，要相信阳光总在风雨后”，分词后结果为：生活 没有 成了 相信 阳光 风雨，然后为每个特征向量赋予权值： 生活(5) 没有(2) 成了(1) 相信(2) 阳光(3) 风雨(2)，其中括号里的数字代表这个单词在整条语句中的重要程度，数字越大代表越重要。

2.hash

通过hash函数计算各个特征向量的hash值，hash值为二进制数01组成的n-bit签名。比如“生活”的hash值Hash(生活)为110101，“没有”的hash值Hash(没有)为“101001”。就这样，字符串就变成了一系列数字。

3.加权

在hash值的基础上，给所有特征向量进行加权，即W = Hash * weight，且遇到1则hash值和权值正相乘，遇到0则hash值和权值负相乘。例如给“生活”的hash值“110101”加权得到：W(生活) = 110101 5 = 5 5 -5 5 -5 5，给“没有”的hash值“101001”加权得到：W(没有)=101001 2 = 2 -2 2 -2 -2 2，其余特征向量类似此般操作。

4.合并

将上述各个特征向量的加权结果累加，变成只有一个序列串。拿前两个特征向量举例，例如“生活”的“5 5 -5 5 -5 5”和“没有”的“2 -2 2 -2 -2 2”进行累加，得到“5+2 5-2 -5+2 5-2 -5-2 5+2”，得到“7 3 -3 3 -7 7”。

5.降维

对于n-bit签名的累加结果，如果大于0则置1，否则置0，从而得到该语句的simhash值，最后我们便可以根据不同语句simhash的海明距离来判断它们的相似度。例如把上面计算出来的“9 -9 1 -1 1 9”降维（某位大于0记为1，小于0记为0），得到的01串为：“1 1 0 1 0 1”，从而形成它们的simhash签名。

整个过程的流程图为：
![image](https://github.com/z0911k/interview_questions/assets/76470990/a631e650-038b-4383-844e-cc6efb6c3683)



### 如何判断一个query是视频的query？

### Coding：求字符串的最长无重复子串

## 华为

### 堆排序

### 进程和线程的区别

### 路由和交换机的不同

### Coding 链表的入环节点


## 快手

### 数据流找中位数

## 宁德时代

### （1）遗传算法应该怎么优化？

### （2）小波分解每一层的意义？

在利用傅里叶变化的时候需要用到全部时域的信息，它并不能反应随着时间变化信号频域成分的变化。而短时傅里叶变换时间窗口的宽度不好确定，而小波分解解决了这个问题。
小波分解将傅里叶变换中的基函数进行了替换，将无限长的三角函数替换成有限长并且会衰减的小波基。这样不仅能获取频率还可以定位到时间。

![image](https://github.com/z0911k/interview_questions/assets/76470990/1343b157-0507-4d99-bf4f-913213431cd5)

这里有两个变量，一个是尺度a，另外一个是平移量T。尺度能控制小波函数的伸缩，平移量T控制小波函数的平移，也就是对应于时间。

第一次分解将原始信号分解成了低频和高频的子信号，而第二层是将上一层的低频信号继续分解成低频和高频的信号。总之，每一层分解代表着不同频率，不同层次的细节信息。


## 淘天集团

### top-k top-p 什么含有

### deepseed

### 生成策略

### 全量finetune

### 新的强化学习策略

### langchain分为几个模块

## 百度

### 扔了10次硬币，7次正面朝上，下一次正面朝上的概率是多少？

### 如何解决哈希冲突， python的list数据结构底层是由什么实现的？

## ALBERT

### 一个简化版的的bert，改进主要与下面几点：

### 1、参数共享，使模型更加的scalable，更容易扩展，参数更少，更容易泛化

### 2、Sentence Order Prediction (SOP)句子顺序预测

### 3、优化器为LAMB：Large Adaptive Mini Batches 主要是针对非常大的mini batch size设计的。相比Adam，它可以大大提升速率。

### 4、单个词的masking转化为了Ngram的masking。
