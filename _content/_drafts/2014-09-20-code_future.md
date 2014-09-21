代码的未来

1.2 未来预测

巴纳姆效应 Barnum Effect
心理学现象，指的是将一些放之四海而皆准的、模棱两可的一般性描述放在自己身上，并认为对自己是准确的

IT未来预测，从过去看未来，就是价格下降，性能提高，容量增大，带宽增加
用极限的方式思考，就是未来设备很小，但是计算能力巨大，SSD成为硬盘的替代，带宽使得联网更加方便


2.1 编程语言的世界
编程语言的进化方向

有说法称，大部分人以此只能驾驭7+-2个概念。所以能够让问题处理方式更加抽象，就可以解决更加复杂的问题。

人月神话称“无论什么编程语言，生产一条基本语句所需要的工数几乎是一样的”，所以如果描述同样的算法，A语言要1000行，B要10行，则B语言的效率要高100倍。

在Matz看来，编程语言的进化动机，不是工具和语言本身的简化，而是通过这些工具和语言得到的解决方案更加简洁。
所以100年的语言应该会更加强调What，对于如何解决问题的How部分，不再需要过多过问。

20年后的编程语言
20年后的语言应该是在分布处理（多计算机协作）和并行处理（多CPU协作）功能上强化，使得开发者不需要特别花心思使用这些功能。
不过我认为现在的线程、RPC等显示使用分布处理和并行处理的形式，早晚晚会遇到瓶颈。当核心超过数千个的时候，显示指定就变得毫无意义了，调试起来也会非常痛苦。

2.4 内存管理 精彩的一节
内存不是无限的，有时需要和虚拟内存来交换，但这种交换对性能影响极大。

GC就是将不再需要的内存空间还给系统，如果不小心访问这些空间的话，会导致别的程序数据被改写，程序出现异常行为甚至崩溃。

GC用到的两个术语是 垃圾（需要被回收的对象）和根（判断对象是否可用的起点，如变量和运行栈空间）

GC算法：
1. 标记删除（改进是标记压缩），该算法的缺点是，如果分配了大量对象，只有一小部分存活，消耗时间会很大，因为清楚阶段需要扫描大量死亡对象。
2. 复制收集，该算法是将可用对象复制到新的空间。不过在存活对象比例较大的时候，会比较不利。该算法的一个好处是具有局部性。在复制收集过程中，会按照对象引用顺序复制到新空间，所以关系较近的对象会放在内存较近的空间的可能性会增大。此时内存缓存更容易有效工作，程序运行性能会提高。
3. 引用计数是最容易实现的方式之一，实现简单，中断时间少是优点。缺点是循环引用、不能漏掉计数以及不适用于并行处理。

GC的算法都是这三种方式的衍生品，更高级的方式是：
1. 分代回收，一般只对新生代进行回收操作，即小GC，必要时进行大GC或Full GC
分代回收通过减小GC中扫描的对象数量，达到缩短GC平均时间的效果，不过由于还要进行大回收，所以最大中断时间没有改善。从吞吐量上来说，在对象寿命假说成立的程序中，扫描对象减少，可以达到不错的成绩。但是会受到程序行为、分代数量、大回收触发条件等因素的大幅度影响
2. 增量回收，用于实时系统。由于是分布渐进的，所以中断时间可以得到控制，但是终占有时间增加，导致总GC时间增加。
3. 并行回收，基本原理是在原程序运行同时进行GC，不过并行回收也需要写屏障来对当前状态保持更新，而且也做不到完全并行，在某些阶段还需要原程序暂停。
目前并行算法在不断改进，而且在硬件系统支持下，无需中断原程序的完全并行回收也呼之欲出，这个领域很值得期待

GC大统一理论
标记清楚、复制收集这种从根开始判断的算法称之为跟踪回收（Tracing GC），相对的是引用计数，2004年的《A Unified Theory of Garbage Collection》论文中说，任何GC算法都是这两种思路的组合，两者互相独立，改善一方必然存在对另一方进行改善的技术
例如改善分代护手和增量回收的写屏障，就是吸取了引用回收的思路etc


2.6 闭包 TODO


P169 布隆过滤器 bloom filter
判断某个数据是否存在的数据结构，特点是时间O(1)，空间也很好，无法删除，小概率下会出错

DHT 分布式散列
算法如CAN、Chord、Pastry、Tapestry等
实现的kv数据库如 couchdb、tokyotyrant、kai、roma等


4.2 C10K问题 TODO 


4.3 HashFold TODO
是Mapreduce的变体，”improve mapreduce with hashfold“

4.5 rack和unicorn TODO


5.1 kv存储 TODO

5.4 SQL的反击TODO

voltDB

5.5 mem redis TODO

6.2 Unix管道 TODO

6.3 非阻塞IO TODO

6.4 Nodejs

6.5 zeromq


























