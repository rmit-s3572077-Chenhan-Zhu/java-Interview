# java-Interview

J2SE基础：

<h3>1. 九种基本数据类型的大小，以及他们的封装类。</h3>
Void		Integer(4)	Float(4) 	Double(8)	Char(2)	Byte(1)	
void 	            Int		float		double		char 		byte
Short(2)	Long(8)	Boolean
short 		long		boolean

<h3>2. Switch能否用string做参数？</h3>
可以，以及其他可以转换为int的数据类型，boolean。

<h3>3. equals与==的区别。</h3>
Equals 在不重写的情况下和==相同，如果A对象equals B对象那么它们的hashcode也相等，但hashcode相等无法推出它们equals，

对于值变量（int、float、double、char等），用“==”来判断相等性。
对于String，用“==”来判断字符串地址是否相等，用“equals()”来判断字符串内容是否相等。
对于引用对象，用“==”来判断对象地址是否相等，经常覆写equals方法，让开发者自己去定义满足什么条件的两个Object是equal的。

<h3>4. Object有哪些公用方法？</h3>
clone(): 对对象的浅复制，创建并返回此对象的一个副本。
wait():导致当前线程等待，放弃线程锁，等待notif或notifyall唤醒进入就绪状态。
Notify:唤醒在此对象监视器上等待的单个线程。
Notifyall:唤醒在此对象监视器上等待的所有线程。
Equals:
Hashcode: 返回该对象的哈希码值。


<h3>5. Java的四种引用，强弱软虚，用到的场景。</h3>
强引用：new出来的便是强引用，无法被gc回收，垃圾回收器不会回收有强引用的对象，
即使OutOfMemoryError(内存空间不足)也不会回收。

软引用：如果内存空间足够，垃圾回收器就不会回收它。软引用的作用：软引用可用来实现内存敏感的高速缓存。浏览器的后退按钮。按后退时，这个后退时显示的网页内容是重新进行请求还是从缓存中取出呢。

弱引用：一旦发现了只具有弱引用的对象，不管当前内存空间足够，垃圾回收期都会回收它。

虚引用：在任何时候都可能被垃圾回收器回收。


<h3>6. Hashcode的作用。</h3>
hashCode的存在主要是用于查找的快捷性, 判断对象是否存在集合中, 重写equals方法的同时也要重写hashCode方法

<h3>7. ArrayList、LinkedList、Vector的区别。</h3>
Arraylist 是连续的顺序存储结构，在查询时速度较快，可改变大小的数组.当元素加入时,其大小将会动态地增长。
Linkedist 是链式存储结构，在添加及删除节点时觉快
Vector是线程安全、同步的结构，和ArrayList类似，但性能较差。

<h3>8. String、StringBuffer与StringBuilder的区别。</h3>
String ：不可变的对象, 因此在每次对 String 类型进行改变的时候其实都等同于生成了一个新的 String 对象，
StringBuffer:线程安全，性能较差，适合在多线程中使用
StringBuilder：非线程安全，性能较好，

<h3>9. Map、Set、List、Queue、Stack的特点与用法。</h3>
Map：分为key和value键值对，key值不可重复
Set： 不可重复，最多一个null元素，包括hashset和treeset。
List：允许有重复值。包括 ArrayList、LinkedList、Vector。
Queue：先进先出的队列 包括offer、poll、peek等。
Stack： 后进先出的栈。包括push、pop、peek、empty、search等。


<h3>10. HashMap和HashTable的区别。</h3>
HashMap:非线程安全，性能较好，允许null值，fail-fast
HashTable：线程安全，性能较差，不允许null值，非fail-fast

Fail-fast: 当某一个线程A通过iterator去遍历某集合的过程中，若该集合的内容被其他线程所改变了；那么线程A访问集合时，就会抛出ConcurrentModificationException异常，产生fail-fast事件。

<h3>11. HashMap和ConcurrentHashMap的区别，HashMap的底层源码。</h3>
HashMap:非线程安全

ConcurrentHashMap：线程安全，一个ConcurrentHashMap由多个Segment组成，每一个Segment都包含了一个HashEntry数组的hashtable,每个Segment包含了自己的hashtable的操作

<h3>12. TreeMap、HashMap、LindedHashMap的区别。</h3>
HashMap: 根据键的HashCode 值存储数据,根据键可以直接获取它的值，具有很快的访问速度，遍历时，取得数据的顺序是完全随机的

TreeMap: TreeMap实现SortMap接口，能够把它保存的记录根据键排序,默认是按键值的升序排序，TreeMap多了一个排序的功能.

LindedHashMap:可以保证HashMap集合有序。存入的顺序和取出的顺序一致。

<h3>13. Collection包结构，与Collections的区别。</h3>

Collection是单列集合，是集合类的上级接口，子接口主要有Set和List、Map。

Collections是针对集合类的一个帮助类，提供了操作集合的工具方法：一系列静态方法实现对各种集合的搜索、排序、替换和线程安全化等操作。

<h3>14. try catch finally，try里有return，finally还执行么？</h3>
如果在try语句里有return语句，finally语句还是会执行。它会在把控制权转移到该方法的调用者或者构造器前执行finally语句。也就是说，使用return语句把控制权转移给其他的方法前会执行finally语句。

<h3>15. Excption与Error包结构。OOM你遇到过哪些情况，SOF你遇到过哪些情况。</h3>



Throwable包含两个子类: **Error **和 **Exception **。它们通常用于指示发生了异常情况。
Java将可抛出(Throwable)的结构分为三种类型： 被检查的异常(Checked Exception)，运行时异常(RuntimeException)和错误(Error)。

ArithmeticException（除数为0的异常）, BufferOverflowException（缓冲区上溢异常）, ClassCastException（强制转换异常）, IndexOutOfBoundsException（出界异常）, NullPointerException（空指针异常）, EmptyStackException（空栈异常）, IllegalArgumentException（不合法的参数异常）

ERROR： 当资源不足、约束失败、或是其它程序无法继续运行的条件发生时，就产生错误。程序本身无法修复这些错误的。例如，VirtualMachineError就属于错误。出现这种错误会导致程序终止运行。OutOfMemoryError（内存溢出）、ThreadDeath， unknownerror。、

OOM(内存溢出): 扩展栈时无法申请到足够内存，主要有2个原因：内存泄露和内存溢出，可由堆异常，虚拟机和本地方法溢出，方法区溢出导致。

SOF(栈溢出): 全名StackOverFlowError，主要由递归调用，
大量循环或死循环，
全局变量是否过多数组


<h3>16. Java面向对象的三个特征与含义。</h3>

封装：封装就是隐藏一切可隐藏的东西，只向外界提供最简单的编程接口，并增强程序的安全性

继承：继承中最常使用的两个关键字是extends（用于基本类和抽象类）和implements（用于接口）。Java中类的继承是单一继承，若使用extends只允许有一个父类，使用implements则不限

多态：Override（重写）和 Overload（重载）



<h3>17. Override和Overload的含义去区别。</h3>

重写Override：存在于父类和子类之间，参数列表必须完全与被重写的方法相同，子类方法不能缩小父类方法的访问权限

重载Overload：参数类型、个数、顺序至少有一个不相同。在类中可以创建多个方法，它们具有相同的名字，但具有不同的参数和不同的定义。

<h3>18. Interface与abstract类的区别。</h3>

抽象类：一个类没有包含足够多的信息来描述一个具体的对象，这样的类就是抽象类。不能被实例化。

接口：接口是个集合，并不是类，不能被实例化，可由implements实现，接口中的方法必须是抽象的

区别：
抽象类可以有默认的方法实现完全是抽象的。接口根本不存在方法的实现。  

抽象类可以有构造器，而接口不能有构造器   

抽象方法可以有public、protected和default这些修饰符 接口方法默认修饰符是public。你不可以使用其它修饰符。

<h3>19. Static class 与non static class的区别。</h3>

静态类： 用static修饰 只包含静态类成员 不可以包含实例成员 使用类名调用静态成员 不能被实例化 不能包含实例构造函数 

非静态类：不用static修饰 可以包含静态类成员 可以包含实例成员 使用实例对象调用非静态类成员 可以被实例化 包含实例构造函数


<h3>20. Java多态的实现原理。</h3>

动态绑定； 指在执行期间判断所引用对象的实际类型，根据其实际的类型调用 其相应的方法



<h3>21. 实现多线程的两种方法：Thread与Runable。</h3>

Thread：资源不共享，而runable资源共享

以实现Runnable接口为主，因为实现Runnable接口相比继承Thread类有如下优势： 1、可以避免由于Java的单继承特性而带来的局限； 2、增强程序的健壮性，代码能够被多个线程共享，代码与数据是独立的；

<h3>22. 线程同步的方法：sychronized、lock、reentrantLock等。</h3>

区别：
用法上的不同：
synchronized既可以加在方法上，也可以加载特定代码块上，而lock需要显示地指定起始位置和终止位置。
synchronized是托管给JVM执行的，lock的锁定是通过jdk代码实现的，它有比synchronized更精确的线程语义。
性能上的不同：
lock接口的实现类ReentrantLock，不仅具有和synchronized相同的并发性和内存语义，还多了锁投票、定时锁、等候和中断锁等。
在竞争不是很激烈的情况下，synchronized的性能优于ReentrantLock，竞争激烈的情况下synchronized的性能会下降的非常快，而ReentrantLock则基本不变。
锁机制不同：
synchronized获取锁和释放锁的方式都是在块结构中，当获取多个锁时，必须以相反的顺序释放，并且是自动解锁。而Lock则需要开发人员手动释放，并且必须在finally中释放，否则会引起死锁。




<h3>23. 锁的等级：方法锁、对象锁、类锁。</h3>


1、对象锁（方法锁）
当一个对象中有同步方法或者同步块，线程调用此对象进入该同步区域时，必须获得对象锁。如果此对象的对象锁被其他调用者占用，则进入阻塞队列，等待此锁被释放（同步块正常返回或者抛异常终止，由JVM自动释放对象锁）。
注意，方法锁也是一种对象锁。当一个线程访问一个带synchronized方法时，由于对象锁的存在，所有加synchronized的方法都不能被访问（前提是在多个线程调用的是同一个对象实例中的方法）。

2、类锁
一个class其中的静态方法和静态变量在内存中只会加载和初始化一份，所以，一旦一个静态的方法被申明为synchronized，此类的所有的实例化对象在调用该方法时，共用同一把锁，称之为类锁。



<h3>24. 写出生产者消费者模式。</h3>
<h3>25. ThreadLocal的设计理念与作用。</h3>
<h3>26. ThreadPool用法与优势。</h3>
<h3>27. Concurrent包里的其他东西：ArrayBlockingQueue、CountDownLatch等等。</h3>
<h3>28. wait()和sleep()的区别。</h3>
<h3>29. foreach与正常for循环效率对比。</h3>
<h3>30. Java IO与NIO。</h3>
 
传统IO处理数据就像“小鸡啄米”，而NIO则是“狼吞虎咽”。
NIO中引入了缓冲区的概念，缓冲区作为传输数据的基本单位块，所有对数据的操作都是基于将数据移进/移出缓冲区而来；读数据的时候从缓冲区中取，写的时候将数据填入缓冲区。尽管传统JavaIO中也有相应的缓冲区过滤器流（BufferedInputStream等），但是移进/移出的操作是由程序员来包装的，它本质是对数据结构化和积累达到处理时的方便，并不是一种提高I/O效率的措施。NIO的缓冲区则不然，对缓冲区的移进/移出操作是由底层操作系统来实现的。
除了效率上的差别外，缓冲区在数据分析和处理上也带来的很大的便利和灵活性。
 
阻塞与非阻塞IO
传统JavaIO是基于阻塞I/O模型。这意味着，当一个线程调用read() 或 write()时，该线程被阻塞，直到有一些数据被读取，或数据完全写入。该线程在此期间不能再干任何事情了。 Java NIO的非阻塞模式，使一个线程从某通道发送请求读取数据，但是它仅能得到目前可用的数据，如果目前没有数据可用时，就什么都不会获取。而不是保持线程阻塞，所以直至数据变的可以读取之前，该线程可以继续做其他的事情。 非阻塞写也是如此。一个线程请求写入一些数据到某通道，但不需要等待它完全写入，这个线程同时可以去做别的事情。 线程通常将非阻塞IO的空闲时间用于在其它通道上执行IO操作，所以一个单独的线程现在可以管理多个输入和输出通道（channel）。


<h3>31. 反射的作用于原理。</h3>

反射可以调用自身，查看自身的方法

<h3>32. 泛型常用特点，List<String>能否转为List<Object>。</h3>
<h3>33. 解析XML的几种方式的原理与特点：DOM、SAX、PULL。</h3>
<h3>34. Java与C++对比。</h3>
<h3>35. Java1.7与1.8新特性。</h3>
<h3>36. 设计模式：单例、工厂、适配器、责任链、观察者等等。</h3>
<h3>37. JNI的使用。</h3>
