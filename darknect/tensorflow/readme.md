# tensorflow  使用

[TFLearn: Deep learning library featuring a higher-level API for TensorFlow ](https://github.com/Ewenwan/tflearn)

[Learn_TensorFLow](https://github.com/Ewenwan/Learn_TensorFLow)

[TensorFlow技术内幕（一）：导论](https://www.imooc.com/article/265350)

![](https://upload-images.jianshu.io/upload_images/12714329-6928cb6461e05052.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/565/format/webp)

    TensorFlow 是一个使用 数据流图 (Dataﬂow Graph)  表达数值计算的开源软件库。
    用 节点 表示抽象的 数学计算，并使用 OP 表达计算的逻辑；
    而 边   表示节点间 传递的数据流，
    并使用 Tensor 表达数据的表示。
    数据流图是一种有 向无环图 (DAG)，当图中的 OP 按照特定的拓扑排序依次被执行时，
    Tensor 在图中流动形成数据流， TensorFlow 因此而得名。
    
    分布式运算： 数据流图的被分裂为多个子图，
                 在一个机器内，注册的子图被二次分裂为更小的子图，
                 它们被部署在本地设备集上并发执行。
    
    TensorFlow 最初由 Google Brain (谷歌大脑) 的研究员和工程师们开发出来，
    用于开展机器学习和深度神经网络的研究，
    包括 语言识别、计算机视觉、自然语言理解、机器人、信息检索。
    
    Google Brain 构建了第一代分布式深度学习框架 DistBelief。
    于 2015.11 重磅推出第二代分布式深度学习框架 TensorFlow。
    
    Tensorflow前端支持多种开发语言，包括Python,C++，Go,Java等，出于性能的考虑，后端实现采用了C++和CUDA。

示例:

```python
import tensor flow as tf
# 生成一个1维度向量，长度为10，初始化为0
b = tf.Variable(tf.zeros([10])) 

#生成一个二维数组，大小为784x10,随机初始化 -1~1
W = tf.Variable(tf.random_uniform([784,10],-1,1)) 

# 生成输入的Placeholder，计算的时候填入输入值
x = tf.palceholder(name="x") # tf.placeholder 定义了一个占位的 OP
# 当 Session.run 时，将通过 feed_dict 的字典提供一个 mini-batch 的
# 样本数据集，从而自动推导出 tf.placeholder 的大小。


#计算最终输出
s  = tf.matmul(W,x) + b
out= tf.nn.relu(s)
#开始计算
with tf.Session() as sess:
    r = sess.run(out, feed_dict={x:input})
    print(r)

# 我们我们算法是输入是 x, 输出是 out = Relu(wx+b) .
# MNIST 拥有 50000 个训练样本，如果 batch_size 为 100，
# 则需要迭代 500 次才能完整地遍历一次训练样本数据集，常称为一个 epoch 周期。

```

![](https://upload-images.jianshu.io/upload_images/12714329-664b59dc942586c9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/330/format/webp)

1. 计算图(graph)：TensorFlow中的计算都可以表示为一个有向图(directed graph),上图就是一个计算图(Graph)。

2. 节点(node)：计算图中的每个运算操作，比如Add,Relu,Matmul就将作为节点，b,w,x,out等也是节点

3. 运算(operation)：例如Add,Relu,Matmul，运算代表一种类型的抽象运算。运算可以有自己的属性，但是所有属性必须被预先设置，或则能在计算的时候被推断出来。

4. 运算核：是一个运算在一个具体硬件(GPU,CPU,ARM等)上的实现。

5. 张量（Tensor）：张量是对Tensorflow中所有数据的抽象，张量有自己的维度和size。有自己是数据类型，比如浮点，整形等。张量沿着计算图的边流动，这也是平台名称tensorflow名字的来源。

6. 会话（session）：会话包含了计算图运行的所有上线问信息。



# tensorflow  pip安装
    Ubuntu/Linux 64-bit$ 
    安装 python
          sudo apt-get install python-pip python-dev

          linux 查看python安装路径,版本号安装路径：
          which python版本号:  python

    简单pip安装 
          python2：
          pip install tensorflow==1.4.0      cpu版本
          pip install tensorflow-gpu==1.4.0  gpu版本

          python3：
          pip3 install tensorflow==1.4.0
          pip3 install tensorflow-gpu==1.4.0

    复杂pip安装
          python2.7 
               安装 0.8.0    cpu版本
               sudo pip install --upgrade https://storage.googleapis.com/tensorflow/linux/cpu/tensorflow-0.8.0-cp27-none-linux_x86_64.whl

               安装新 0.12.0rc1 cpu版本
               sudo pip install --upgrade https://storage.googleapis.com/tensorflow/linux/cpu/tensorflow-0.12.0rc1-cp27-none-linux_x86_64.whl

          python3.4
          安装 0.8.0   cpu版本
            sudo pip3 install --upgrade https://storage.googleapis.com/tensorflow/linux/cpu/tensorflow-0.8.0-cp34-cp34m-linux_x86_64.whl

          1.4版本   cpu版本
            sudo pip3 install --upgrade https://storage.googleapis.com/tensorflow/linux/cpu/tensorflow-1.4.0-cp34-cp34m-linux_x86_64.whl


    安装新 版本前需要卸载旧版本
    sudo pip uninstall TensorFlowsudo pip uninstall protobuf 
    
# tensorflow  源码安装
    最新 的软件仓库安装 不包含一些最新的功能
    ubuntu 软件仓库 https://packages.ubuntu.com/
    
    github 源码安装源码安装介绍
    http://blog.csdn.net/masa_fish/article/details/54096996
    
    TensorFlow技术内幕（二）：编译与安装
    https://www.imooc.com/article/265349

# 学习tensorflow 目录
```asm
* 1. [Simple Multiplication] 两个数相乘 相加 (00_multiply.py) 
* 2. [Linear Regression]     两维变量 线性回归  (01_linear_regression.py)
                             三维变量 线性回归  (01_linear_regression3.py)
       三维变量线性回归 tensorboard 显示优化记录 (01_linear_regression3_graph.py)
* 2. [Logistic Regression]   手写字体 逻辑回归(仅有权重)   (02_logistic_regression.py)
                             手写字体 逻辑回归(权重+偏置)  (02_logistic_regression2.py)
                              tensorboard 显示优化记录    (02_logistic_regression2_tf_board_graph.py
* 3. [Feedforward Neural Network] 多层感知机 无偏置               (03_net.py)
                                  多层感知机 有偏置               (03_net2.py)
* 4. [Deep Feedforward Neural Network] 多层网络 两层 隐含层无偏置 (04_modern_net.py)
                                       多层网络 两层 隐含层有偏置 (04_modern_net2.py)
* 5. [Convolutional Neural Network] 卷积神经网络 无偏置           (05_convolutional_net.py)
                                    卷积神经网络 有偏置           (05_convolutional_net2.py)
                                    tensorboard 显示优化记录      (05_convolutional_net3_board.py)
* 6. [Denoising Autoencoder]        自编码 原理与PCA相似  单层     (06_autoencoder.py)
                                    自编码 原理与PCA相似  两层     (06_autoencoder2.py)
                                    自编码 原理与PCA相似  四层     (06_autoencoder3.py)
* 7. [Recurrent Neural Network (LSTM)]长短时记忆   单一 LSTM网络   (07_lstm.py)
                                      长短时记忆   LSTM+RNN网络    (07_lstm2.py)
* 8. [Word2vec]                       单词转词向量 英文            (08_word2vec.py)
                                      单词转词向量 中文            (08_word2vec2.py)
* 9. [TensorBoard]                    tensorboard 显示优化记录专题 (09_tensorboard.py)
* 10. [Save and restore net]          保存和载入网络模型           (10_save_restore_net.py)
```

# 1. TensorFlow 前身 DistBelief 分析 
    DistBelief 的编程模型是基于 层 的 DAG 图。
    层可以看做是一种组合多个运算操作符的复合运算符，它完成特定的计算任务。
    例如，全连接层完成 f(W * x + b) 的复合计算，包括
    输入与权重的矩阵乘法，随后再与偏置相加，
    最后在线性加权值的基础上应用激活函数，实施非线性变换。
    
    DistBelief 使用参数服务器 (Parameter Server, 常称为 PS) 的系统架构，
    训练作业包括两个分离的进程：
        1. 无状态的 Worker 进程，用于模型的训练；
        2. 有状态的 PS 进程，用于维护模型的参数。
     
    在分布式训练过程中，
    各个模型副本异步地从 PS 上拉取训练参数 w，
    当完成一步迭代运算后，推送参数的梯度 ∆w 到 PS 上去，
    w' = w - Learning_rate * ∆w 
    并完成参数的更新。

## DistBelief 缺陷:
    但是，对于深度学习领域的高级用户， DistBelief 的编程模型，
    及其基于 PS 的系统架构，缺乏足够的灵活性和可扩展性。
    1. 优化算法：
       添加新的优化算法，必须修改 PS 的实现；
       get(), put() 的抽象方法，对某些优化算法并不高效。
    2. 训练算法：
       支持非前馈的神经网络面临巨大的挑战性；
       例如，包含循环的 RNN，交替训练的对抗网络;
       及其损失函数由分离的代理完成的增强学习模型。
    3. 加速设备：
       DistBelief 设计之初仅支持多核 CPU，并不支持多卡的 GPU，
       遗留的系统架构对支持新的计算设备缺乏良好的可扩展性。 

##  TensorFlow 设计及改进
    TensorFlow 使用数据流图表达计算过程和共享状态，
    使用节点表示抽象计算，使用边表示数据流。
    
    
### 设计原则：
    TensorFlow 的系统架构遵循了一些基本的设计原则，
    用于指导 TensorFlow 的系统实现.
    
    1. 延迟计算：
       图的构造与执行分离，并推迟计算图的执行过程；
       
    2. 原子 OP： 
       OP 是最小的抽象计算单元，支持构造复杂的网络模型；
       
    3. 抽象设备：
       支持 CPU, GPU, ASIC 多种异构计算设备类型；
       
    4. 抽象任务：
       基于任务的 PS（参数服务器），对新的优化算法和网络模型具有良好的可扩展性。
    
### 优势：
    相对于其他机器学习框架， TensorFlow 具有如下方面的优势。
    
    1. 高性能： 
       TensorFlow 升级至 1.0 版本性能提升显著，
       单机多卡 (8 卡 GPU) 环境中， Inception v3 的训练实现了 7.3 倍的加速比；
       在分布式多机多卡 (64 卡 GPU) 环境中， Inception v3 的训练实现了 58 倍的加速比；
       
    2. 跨平台：
       支持多 CPU/GPU/ASIC 多种异构设备的运算；支持台式机，服务器，移动设备等多种计算平台；
       支持 Windows， Linux， MacOS 等多种操作系统；
    3. 分布式：
       支持本地和分布式的模型训练和推理；
    4. 多语言：
       支持 Python, C++, Java, Go 等多种程序设计语言；
    5. 通用性：
       支持各种复杂的网络模型的设计和实现，包括非前馈型神经网络；
    6. 可扩展：
       支持 OP 扩展， Kernel 扩展， Device 扩展，通信协议的扩展；
    7. 可视化：
       使用 TensorBoard 可视化整个训练过程，极大地降低了 TensorFlow 的调试过程；
    8. 自动微分： 
       TensorFlow 自动构造反向的计算子图，完成训练参数的梯度计算；
    9. 工作流： 
       TensorFlow 与 TensorFlow Serving 无缝集成，支持模型的训练、导入、
       导出、发布一站式的工作流，并自动实现模型的热更新和版本管理。
    
# 2. TensorFlow 编程环境
    代码结构，工程构建，理解 TensorFlow 的系统架构
    
## 代码结构
克隆源代码：
> $ git clone git@github.com:tensorflow/tensorflow.git

切换到最新的稳定分支上。例如， r1.4 分支.

> $ cd tensorflow

> $ git checkout r1.4

查看代码结构：
>$ tree -d -L 1 ./tensorflow   目录下 一级目标列表

```
./tensorflow
├── c               C API代码
├── cc              C++ API代码            总53 万行+  C/C++ 代码
├── compiler        XLA,JIT等编译优化相关   大约为 12.5 万行，主要使用 C++ 实现
├── contrib         第三方贡献的代码
├── core            内核代码, 主要由 C++ 实现，大约拥有 26 万行代码
├── docs_src        文档相关文件
├── examples        例子相关代码
├── g3doc           TF文档
├── go              go API相关代码
├── java            java API相关代码
├── python          Python API相关代码   总37 万行+   Python提供的 API 最完善
├── stream_executor 并行计算框架代码，实现了 CUDA 和 OpenCL 的统一封装。  C++ 实现 2.5 万行代码
├── tools           辅助工具工程代码
└── user_ops        tf插件代码
```

    contrib 是第三方贡献的编程库，
    它也是 TensorFlow 标准化之前的实验性编程接口，
    犹如 Boost 社区与 C++ 标准之间的关系。
    当 contrib 的接口成熟后，便会被 TensorFlow
    标准化，并从 contrib 中搬迁至 core, python 中，


core 内核代码 目录：
> tree -d -L 1 ./tensorflow/core

```
./tensorflow/core
├── common_runtime            本地运行时，公共运行库
├── debug                     调试相关
├── distributed_runtime       分布式运行时，分布式执行模块
├── example                   例子代码
├── framework                 基础框架，基础功能模块
├── graph                     图操作，计算图相关
├── grappler                  模型优化模块 Grappler
├── kernels                   Kernel 实现，包括CPU和GPU上的实现
├── lib                       公共基础库
├── ops                       OP 定义，操作代码
├── platform                  各种平台实现相关 
├── profiler
├── protobuf                  Protobuf 定义
├── public
├── user_ops                  OP 定义
└── util                      实用函数库？
```

 Python API相关代码 目录： 大约有 18 万行代码
> tree -d -L 1 ./tensorflow/python         

```
./tensorflow/python
├── client          客户端?
├── debug
├── estimator
├── feature_column
├── framework
├── grappler
├── kernel_tests
├── layers
├── lib
├── ops
├── platform
├── profiler
├── saved_model
├── summary
├── tools
├── training
├── user_ops
└── util
```


