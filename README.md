# COMPX201 / Y05335 - 期中复习 - A部分知识点

## 知识点 1: 递归 (Recursion) - 对应问题 1

**问题1回顾:** 识别递归函数中的停止条件。
   * **正确答案:** `if(n==1){ return 1; }`

**讲义扩充与复习 (参考 "Week 5 - Recursion.pdf"):**

* **递归的定义:**
    * 一个递归方法是指在其定义中调用自身的方法 (Week 5, Slide 4)。
    * 通过递归解决问题，意味着重复执行相同的函数，直到达到一个停止条件 (Week 5, Slide 4)。

* **递归方法的三个要素 (Week 5, Slide 4):**
    1.  **停止条件 (Stopping condition / Base case):** 递归必须有的部分，定义递归何时结束，防止无限调用。阶乘例子中，`n` 达到1是停止条件。缺少会导致“栈溢出 (stack overflow)” (Week 5, Slide 25)。
    2.  **问题规模的缩小 (Reduction of problem):** 每次递归调用，问题应向停止条件靠近。阶乘例子中，`factorialR(n-1)` 使问题规模从 `n` 缩小到 `n-1`。
    3.  **递归调用 (Recursive Call):** 方法调用自身。

* **递归的类型 (Week 5, Slides 9, 30, 33, 36, 39, 342, 348):**
    * **线性递归 (Linear recursion):** 每次调用最多一次递归调用 (如阶乘) (Week 5, Slide 10, 30)。
    * **尾递归 (Tail recursion):** 递归调用是方法最后执行的语句 (特殊的线性递归) (Week 5, Slide 13)。
    * **二叉递归 (Binary recursion):** 每次调用至少两次递归调用 (如BST的某些操作) (Week 5, Slide 14, 67)。
    * **指数递归 (Exponential recursion):** 调用次数与数据集大小成指数关系 (Week 5, Slide 16)。
    * **嵌套递归 (Nested recursion):** 递归函数的参数是递归函数本身 (如阿克曼函数) (Week 5, Slide 18)。
    * **相互递归 (Mutual recursion):** 两个或多个递归函数相互调用 (Week 5, Slide 21)。

* **递归的开销 (Week 5, Slides 24-26):**
    * Java通过调用栈实现方法调用，每个调用对应一个活动记录。
    * 递归可能占用大量栈空间，导致栈溢出。
    * 若循环能胜任，应避免递归。

---

## 知识点 2: 二叉搜索树 (Binary Search Tree - BST) - 对应问题 2, 9, 10

**问题2回顾:** 计算BST中节点的深度。
   * **正确答案:** 2 (节点45的深度)

**问题10回顾:** 创建BST副本最常用的遍历方法。
   * **正确答案:** 先序遍历 (Pre-order traversal)

**讲义扩充与复习 (参考 "Week 4 - Binary Search Trees I.pdf"):**

* **BST的定义与结构 (Week 4, Slides 4-5):**
    * 支持对数时间搜索的抽象数据类型。
    * 顶层节点是**根 (root)**。
    * 每个节点有值和两个子树（左、右）。
    * 左子树所有节点值 **小于** 父节点值。
    * 右子树所有节点值 **大于** 父节点值。
    * 每个子树也是BST。
    * 无子节点为**叶节点 (leaf)** (Week 4, Slide 5, 11)。
    * 父节点 (parent) 与 子节点 (children) (Week 4, Slide 5, 10)。
    * 后代 (descendants) 与 祖先 (ancestors) (Week 4, Slide 5, 12-14)。

* **BST的深度 (Depth) 与高度 (Height) (Week 4, Slides 61-65):**
    * **深度 (Depth):** 从根到某节点路径长度，根深度0 (Week 4, Slide 62)。
    * **高度 (Height):** 从某节点到叶节点最长路径长度，叶高度0。空树高-1。树高即根高 (Week 4, Slide 61)。

* **BST操作:**
    * **搜索 (Searching) (Week 4, Slides 18-31):**
        * 从根开始，比较目标值与当前节点值，决定向左或向右子树搜索。
        * 平均搜索时间 $O(\log n)$ (Week 4, Slide 4, 84)。
    * **插入 (Insertion) (Week 4, Slides 32-38):**
        * 空树则新节点为根；否则比较值，递归插入左或右子树。
    * **删除 (Deletion) (Week 4, Slides 39-57):**
        * 叶节点: 直接移除。
        * 单子节点: 用其子节点替换。
        * 双子节点: 用中序后继或前驱替换。
    * **遍历 (Traversal) (Week 4, Slides 66-83):**
        * **中序 (In-order: LNR):** 升序访问 (Week 4, Slide 68, 69-83)。
        * **先序 (Pre-order: NLR):** 常用于复制树 (Week 4, Slide 68)。
        * **后序 (Post-order: LRN):** 常用于删除树 (Week 4, Slide 68)。
        * **层序 (Level-order):** 按层级访问 (Week 4, Slide 68)。

* **BST的平衡 (Balancing) (Week 4, Slide 84):**
    * 左右子树高度尽可能接近。
    * 平衡BST保证 $O(\log n)$ 搜索，不平衡最坏 $O(n)$。
    * AVL树、红黑树是自平衡BST。

---

## 知识点 3: 红黑树 (Red-Black Tree) - 对应问题 3 (概念)

**问题3回顾:** 红黑树中叶节点的颜色。
   * **正确答案:** 黑色 (Black)

**讲义扩充与复习:**

* **红黑树的性质 (通常包括):**
    1.  节点红或黑。
    2.  根节点黑。
    3.  **所有叶子节点（NIL）黑。** (问题3考点)
    4.  红节点的子节点黑 (无连续红)。
    5.  任一节点到其后代叶子的所有路径含相同数目黑节点 (黑高)。
* **目的:** 保持大致平衡，保证操作时间复杂度 $O(\log n)$。

---

## 知识点 4: B树 (B-Tree) - 对应问题 4 (概念)

**问题4回顾:** B树中节点的最大值的数量。
   * **正确答案:** 6 (对于7阶B树)

**讲义扩充与复习:**

* **B树的阶 (Order m):**
    * 节点最多 m 个子节点。
    * 节点最多 m-1 个键（值）。(问题4考点)
    * 内部节点 (除根) 至少 $\lceil m/2 \rceil$ 个子节点。
    * 根节点至少2个子 (除非是叶)。
    * 所有叶节点同层。
* **特点:** 数据排序，允许顺序访问；保持平衡；树高低，适合磁盘。

---

## 知识点 5: 栈 (Stack) - 对应问题 5

**问题5回顾:** 描述栈的peek操作。
   * **正确答案:** 返回栈顶元素但不移除它。

**讲义扩充与复习:**

* **栈的定义:**
    * 后进先出 (Last-In, First-Out - LIFO) 线性数据结构。
    * 操作限“栈顶 (top)”。
* **基本操作:**
    * **Push (压入):** 栈顶添加元素。
    * **Pop (弹出):** 移除并返回栈顶元素。
    * **Peek (查看):** 返回栈顶元素，不移除。(问题5考点)
    * **isEmpty (判空):** 检查是否为空。
* **应用:** 函数调用、表达式求值、括号匹配、DFS、撤销/重做。

---

## 知识点 6: 链表 (Linked List) - 对应问题 6

**问题6回顾:** 链表中指向null的节点的名称。
   * **正确答案:** 尾节点 (Tail node)

**讲义扩充与复习 (参考 "Week 3 - Linked Lists-1.pdf"):**

* **链表的定义 (Week 3, Slide 5):**
    * 有序（或无序）数据元素集合，每元素含指向后继（或前驱）的链接。
    * 自引用数据结构 (Week 3, Slide 6)。
* **组成 (Week 3, Slide 5, 35):**
    * **节点 (Node):** 含数据值 (value) 和指向下一节点的引用 (next)。
    * **头节点 (Head):** 第一个节点。空链表则头为null (Week 3, Slide 5, 35, 63)。
    * **尾节点 (Tail):** 最后一个节点，其 `next` 为 `null` (Week 3, Slide 5, 35)。(问题6考点)
* **类型 (Week 3, Slide 22):**
    * 访问权限: 受限 (如栈队列) (Slide 22) vs. 不受限 (Slide 23)。
    * 顺序: 有序 (Slide 24) vs. 无序 (Slide 25)。
    * 结构: 单向、双向、循环。讲义主讲单向。
* **操作 (Week 3, Slide 11, 28):**
    * add (头/尾/特定位置) (Slides 28, 38-46)。
    * remove (头/尾/特定值) (Slides 61, 85-103)。
    * has (Slides 66-68)。
    * isEmpty (Slides 63-65)。
    * getLength (Slides 69-72)。
    * print (Slides 47-59)。
* **实现 (Week 3, Slide 15-20):**
    * **迭代式 (Iterative):** 用指针引用操作 (讲义Java示例方式) (Slides 16, 18)。
    * **递归式 (Recursive):** 递归定义操作，代码简洁但可能慢且耗内存 (Slide 20)。

---

## 知识点 7: Java基础 - 对应问题 7

**问题7回顾:** Java公共类的文件名。
   * **正确答案:** `Main.java`

**讲义扩充与复习:**

* **文件命名:**
    * Java源码文件以 `.java` 结尾 (Week 3, Slide 81; Week 2, Slide 39)。
    * 若含 `public` 类，文件名须与 `public` 类名完全相同 (含大小写)。
    * 一 `.java` 文件最多一个 `public` 类。
* **编译与运行:** `javac` 编译 `.java` -> `.class`；`java` 运行 `.class`。
* **`main` 方法 (Week 2, Slide 39; Week 3, Slide 81):**
    * Java应用入口点。
    * 标准签名: `public static void main(String[] args)`。

---

## 知识点 8: 队列 (Queue) - 对应问题 8

**问题8回顾:** 描述一种在一端添加、另一端移除的数据结构。
   * **正确答案:** 队列 (Queue)

**讲义扩充与复习:**

* **队列的定义:**
    * 先进先出 (First-In, First-Out - FIFO) 线性数据结构。
    * 元素从“尾部 (rear/back)”加入，从“头部 (front/head)”移除。(问题8考点)
    * 讲义中为受限链表 (Week 3, Slide 22)。
* **基本操作:**
    * **Enqueue (入队):** 尾部添加元素。
    * **Dequeue (出队):** 移除并返回头部元素。
    * **Peek/Front (查看队首):** 返回头部元素，不移除。
    * **isEmpty (判空):** 检查是否为空。
* **应用:** 任务调度、BFS、缓冲区、客服系统。

---

## 知识点 9: AVL树 - 对应问题 9

**问题9回顾:** 判断AVL树的不平衡点。

**讲义扩充与复习 (参考 "Week 6 - AVL in Java.pdf"):**

* **AVL树定义:**
    * 自平衡二叉搜索树。
    * 每节点左右子树高度差 (平衡因子 BF) 最多1 (即 -1, 0, 或 1) (Week 6, Slide 573 暗示)。
* **高度 (Height) (Week 6, Slides 10-14, 581-585):**
    * 节点到叶的最长路径。空子树高-1 (Slides 11, 582)。
    * 非空节点高 = $1 + \max(\text{height(L)}, \text{height(R)})$ (Slides 12-13, 583-584)。
* **平衡因子 (BF) (Week 6, Slides 16-19, 587-590):**
    * BF(node) = height(L) - height(R) (Slides 17, 588)。
    * BF > 1: 左重； BF < -1: 右重。
* **不平衡与旋转 (Week 6, Slides 22-50, 593-632):**
    * 插入/删除致 BF 为 +2 或 -2 时，需旋转恢复。
    * **四种情况与旋转:**
        1.  **左-左 (LL) (BF=+2, 左子BF=+1/0):** 一次**右旋** (Slides 33, 605-609, 670)。
        2.  **右-右 (RR) (BF=-2, 右子BF=-1/0):** 一次**左旋** (Slides 28, 599-603, 670)。
        3.  **左-右 (LR) (BF=+2, 左子BF=-1):** 左子先**左旋**，原节点再**右旋** (双旋) (Slides 38, 611-621, 670)。
        4.  **右-左 (RL) (BF=-2, 右子BF=+1):** 右子先**右旋**，原节点再**左旋** (双旋) (Slides 45, 623-632, 670)。
    * **AVL插入 (Week 6, Slides 60-81, 643-672):**
        * 按BST插入。
        * 从插入点向上回溯，查BF，执行旋转。



# COMPX201 / Y05335 - 期中复习重点整理

## 一、 $O(\log n)$ 时间效率 (对数时间效率)

**核心概念:** 当算法的执行时间（或操作次数）随着输入规模 `n` 的对数增长时，其时间复杂度为 $O(\log n)$。这意味着即使输入规模大幅增加，算法的执行时间增长也非常缓慢。

**二叉搜索树 (BST) 如何支持 $O(\log n)$ 搜索时间 (参考期中问题 2.c):**
* **有序性:** BST 的核心特性是左子节点 < 父节点 < 右子节点。
* **比较与排除:** 每次将目标值与当前节点比较：
    * 相等则找到。
    * 小于则搜索左子树，**完全排除右子树**。
    * 大于则搜索右子树，**完全排除左子树**。
* **搜索空间减半:** 在一个**平衡的或接近平衡的** BST 中，每次比较大约能将待搜索的节点数量减半。
    * 第一次比较后，范围从 `n` 变为约 `n/2`。
    * 第二次比较后，范围从 `n/2` 变为约 `n/4`。
    * 以此类推，直到找到元素或确定元素不存在。
* **对数关系:** 这种每次将问题规模减半的过程，其操作次数与节点总数 `n` 的对数 ($\log_2 n$) 成正比。


**注意:** $O(\log n)$ 的效率依赖于树的平衡性。在最坏情况下（如BST退化成链表），搜索时间会退化到 $O(n)$。

## 二、递归 (Recursion) 的各种知识点
# 递归 (Recursion) - 核心要素与工作原理

## 一、递归的三个核心要素

1.  **基本情况 (Base Case / Stopping Condition - 停止条件):**
    * **是什么？** 这是递归函数中一个或多个可以直接解决问题，而**不再需要进一步递归调用**的条件。它是递归的“出口”或“终点”。
    * **为什么重要？** 如果没有停止条件，递归函数会无限地调用自己，就像一个永不停止的循环，最终会导致“栈溢出 (stack overflow)”错误，因为每次函数调用都会在内存的“调用栈”中占据一些空间。
    * **在阶乘例子 (`factorialR`) 中:** `if(n==1){ return 1; }` 就是停止条件。
        * 当输入的 `n` 等于1时，函数直接返回1，不再调用 `factorialR` 自身。
        * `n=1` 是阶乘问题中可以直接给出答案的最小情况 (1! = 1)。
        * 选项 `a. return 1;` 只是停止条件被满足时执行的*动作*，而不是条件本身。
        * 选项 `d. if(n==1){ return 1; }` 完整地描述了**条件检查 (`if(n==1)`)** 和 **满足条件时的终止行为 (`return 1;`)**，这共同构成了停止条件。

2.  **递归步骤 (Recursive Step / Reduction of Problem - 问题规模的缩小):**
    * **是什么？** 对于不满足基本情况的输入，递归函数会将问题分解成一个或多个与原问题结构相同但“规模更小”的子问题。然后，函数调用自身来解决这些子问题。
    * **为什么重要？** 每次递归调用都必须使问题向基本情况“更近一步”，否则递归也可能不会终止。
    * **在阶乘例子 (`factorialR`) 中:** `return n*(factorialR(n-1));` 是递归步骤。
        * 它将计算 `n!` 的问题，分解为 `n` 乘以计算 `(n-1)!` 的问题。
        * `factorialR(n-1)` 是对自身的调用，但参数是 `n-1`，比原来的 `n` 更小，离基本情况 `n=1` 更近了一步。

3.  **递归调用 (Recursive Call):**
    * **是什么？** 函数调用自身。
    * **在阶乘例子 (`factorialR`) 中:** `factorialR(n-1)` 就是递归调用。

## 二、递归如何工作 (以 `factorialR(3)` 为例)

1.  **`factorialR(3)` 被调用:**
    * `3 == 1` (false)。进入 `else`。
    * 需要返回 `3 * factorialR(2)`。为了得到 `factorialR(2)` 的结果，它**暂停**当前计算，调用 `factorialR(2)`。

2.  **`factorialR(2)` 被调用:**
    * `2 == 1` (false)。进入 `else`。
    * 需要返回 `2 * factorialR(1)`。它**暂停**当前计算，调用 `factorialR(1)`。

3.  **`factorialR(1)` 被调用:**
    * `1 == 1` (true)。**满足停止条件！**
    * 直接 `return 1;`。这个 `1` 会返回给调用它的地方（即 `factorialR(2)` 中等待结果的位置）。

4.  **回到 `factorialR(2)`:**
    * 它收到了 `factorialR(1)` 返回的 `1`。
    * 现在它可以完成计算：`2 * 1`，结果是 `2`。
    * `return 2;`。这个 `2` 会返回给调用它的地方（即 `factorialR(3)` 中等待结果的位置）。

5.  **回到 `factorialR(3)`:**
    * 它收到了 `factorialR(2)` 返回的 `2`。
    * 现在它可以完成计算：`3 * 2`，结果是 `6`。
    * `return 6;`。如果 `factorialR(3)` 是最初的调用，那么 `6` 就是最终结果。

## 三、总结

* **停止条件**是递归的“刹车”，确保递归有终点。
* **递归步骤**是“油门和方向盘”，驱动问题向终点前进。

## 三、AVL树 (Adelson-Velsky and Landis Tree)
## 一、树的高度 (Height)

* **定义:** 从一个节点到其**最远叶子节点**的路径上的**边的数量**。
    * 叶节点高度 = 0。
    * 空子树高度 = -1。
    * `height(node) = 1 + max(height(node.left), height(node.right))`
* **方向:** 节点的“高度”值，**越往上 (朝向根) 值越大**。
* **树的高度:** 指其根节点的高度。
* **关键:** 如果一条从节点到最远叶子的路径上有 `k` 条边，那么该节点的高度就是 `k`。

## 二、AVL树不平衡与旋转

* **平衡因子 (BF):** `BF(节点) = height(节点.左子树) - height(节点.右子树)`
    * AVL树要求：BF $\in \{-1, 0, 1\}$。

* **不平衡类型判断 (P为不平衡点, C为P的较高子节点):**
    * **左-左 (LL):** `BF(P) = +2` (P左重 L), `BF(C = P.left) = +1` (C左倾 L)
        * **旋转:** 对P进行**右旋转**。
    * **右-右 (RR):** `BF(P) = -2` (P右重 R), `BF(C = P.right) = -1` (C右倾 R)
        * **旋转:** 对P进行**左旋转**。
    * **左-右 (LR):** `BF(P) = +2` (P左重 L), `BF(C = P.left) = -1` (C右倾 R)
        * **旋转:** **左-右双旋转** (先对C左旋，再对P右旋)。
    * **右-左 (RL):** `BF(P) = -2` (P右重 R), `BF(C = P.right) = +1` (C左倾 L)
        * **旋转:** **右-左双旋转** (先对C右旋，再对P左旋)。

## 三、树的遍历方式及其应用

1.  **先序遍历 (Pre-order: 根-左-右 / NLR):**
    * **访问顺序:**
        1.  处理当前节点 (N)。
        2.  递归遍历左子树 (L)。
        3.  递归遍历右子树 (R)。
    * **应用场景:**
        * **复制树 (常用)。**
        * 获取表达式树的前缀表示。

2.  **中序遍历 (In-order: 左-根-右 / LNR):**
    * **访问顺序:**
        1.  递归遍历左子树 (L)。
        2.  处理当前节点 (N)。
        3.  递归遍历右子树 (R)。
    * **应用场景:**
        * **对二叉搜索树 (BST) 进行排序输出 (结果为升序序列)。**

3.  **后序遍历 (Post-order: 左-右-根 / LRN):**
    * **访问顺序:**
        1.  递归遍历左子树 (L)。
        2.  递归遍历右子树 (R)。
        3.  处理当前节点 (N)。
    * **应用场景:**
        * **删除树/释放节点内存 (必须先处理子节点)。**
        * 获取表达式树的后缀表示 (逆波兰式)。

4.  **层序遍历 (Level-order / Breadth-First Traversal - BFS):**
    * **访问顺序:** 从根节点开始，逐层访问节点，每层从左到右。
    * **实现:** 通常使用**队列 (Queue)**。
    * **应用场景:**
        * 查找最短路径 (在无权图中或某些树的层级问题)。
        * 按层级打印树的结构。

## 四、B树 (B-Tree)
# B树 (B-Tree) - 核心特性与插入操作

## 一、B树的阶 (Order `m`) 与节点容量

* **阶 (`m`) 的定义:**
    * 一个B树的阶 `m` 定义了每个节点可以拥有的**最大子节点数**。
* **键的数量 (Keys/Values):**
    * 每个节点**最多**可以有 `m-1` 个键。
    * _(例如，5阶B树，每个节点最多有 4 个键。)_
* **子节点数量 (对于非叶节点):**
    * 如果一个节点有 `k` 个键，那么它将有 `k+1` 个子节点。
    * 因此，如果一个节点最多有 `m-1` 个键，它最多将有 `(m-1)+1 = m` 个子节点 (这与阶的定义一致)。
* **最小键数 (对于非根、非叶节点):**
    * 最少 $\lceil m/2 \rceil - 1$ 个键。
* **最小子节点数 (对于非根、非叶节点):**
    * 最少 $\lceil m/2 \rceil$ 个子节点。

## 二、B树的插入操作与节点分裂

1.  **查找插入位置:**
    * 从根节点开始，沿着合适的路径向下查找，直到找到一个叶节点，新键应该插入到这个叶节点中。

2.  **向叶节点插入键:**
    * 将新键按顺序插入到目标叶节点中。

3.  **处理节点满溢 (Node Overflow) - 分裂 (Split):**
    * **条件:** 如果插入新键后，一个节点（无论是叶节点还是内部节点，在键被提升后可能发生）包含的键数量达到了 `m` 个 (即超过了 `m-1` 的上限)。此时节点必须**分裂**。
    * **分裂过程:**
        1.  **选择中间键:** 从 `m` 个键中选择中间的那个键。对于奇数个键，中间键是唯一的；对于偶数个键（如果 `m` 是偶数，分裂前的临时节点有 `m` 个键），通常选择第 $\lceil m/2 \rceil$ 个键。
            * _(例如，5阶B树，节点满了会有5个键，中间键是第5/2=2.5，2.5向上取=3 个键。)_
        2.  **提升中间键:** 将选定的中间键**提升 (promoted)**到其**父节点**中，并按顺序插入。
        3.  **节点分裂:** 原来的满节点（现在已经移除了中间键，剩下 `m-1` 个键）分裂成**两个新的节点**：
            * 一个新节点包含所有**小于**被提升的中间键的键。
            * 另一个新节点包含所有**大于**被提升的中间键的键。
        4.  **重排子节点 (如果是内部节点分裂):** 原来满节点的子节点也需要根据它们与被提升键和新分裂出的两个节点的关系重新分配。
        5.  **连接新节点:** 这两个新分裂出的节点成为原父节点中，被提升键两侧的**直接子节点**。

4.  **级联分裂 (Cascading Splits):**
    * 如果中间键被提升到父节点，而导致父节点也满了，那么父节点也需要按照同样的规则进行分裂。
    * 这个分裂过程可能会一直向上传播，直到根节点。
    * 如果根节点也分裂，一个新的根节点将被创建（只包含一个从原子树提升上来的键），树的高度会增加一层。

**B树特性概览:**
* **自平衡:** 通过分裂和（在删除时可能发生的）合并操作来保持平衡。
* **所有叶节点在同一层级。**
* **磁盘I/O友好:** 节点容量大，树高低，减少磁盘读写次数。

## 五、红黑树
# 红黑树 (Red-Black Tree) - 核心属性与记忆口诀

## 一、核心概念

红黑树是一种自平衡的二叉搜索树 (BST)，它通过为每个节点分配颜色（红色或黑色）并遵循一组特定的属性来确保树大致平衡。这保证了查找、插入和删除等操作的平均和最坏情况时间复杂度为 $O(\log n)$。

## 二、记忆口诀：“根叶黑，不红红，黑路同”

这个口诀帮助我们记住红黑树的关键属性：

1.  **“根叶黑”**
    * **根 (Root) 黑:**
        * **对应属性：** 属性2 - 根节点是黑色的。
        * **解释：** 树的起始点（根节点）必须是黑色。如果操作导致根节点变红，最后会强制其变黑。
    * **叶 (Leaf) 黑:**
        * **对应属性：** 属性3 - 所有叶子节点（NIL节点，即外部空节点）都是黑色的。
        * **解释：** 概念上的NIL叶子节点被视为黑色，这简化了对“黑高”的计算和维护。

2.  **“不红红”**
    * **对应属性：** 属性4 - 如果一个节点是红色的，则它的两个子节点都是黑色的。
    * **解释：** 这条规则确保了从根到叶的任何简单路径上**不会出现两个连续的红色节点**。红色节点不能有红色的父节点或红色的子节点。

3.  **“黑路同”**
    * **对应属性：** 属性5 - 对于每个节点，从该节点到其所有后代叶子节点的简单路径上，均包含相同数目的黑色节点（这个数目称为该节点的“黑高”，black-height）。
    * **解释：** 这是红黑树平衡性的核心保证。从任一节点出发，到达任何一个NIL叶子的路径所经过的黑色节点数量是相同的。




## 概念解释类题目复习：

## 1. 队列的适用性 (Queues)

**Q: Justify why a Queue is better suited for a customer support ticketing system.**
**问：解释为什么队列更适合客户支持工单系统。**

* **EN (学生式答案):** "Choose Queue because a ticketing system needs **first-come, first-served (FIFO)**. New tickets go to the back, and are processed from the front, ensuring fairness. A Stack is last-in, first-out, which is wrong for this."
* **中文 (学生式答案):** “选择队列是因为工单系统要求**先来的先处理 (先进先出)**。新工单加到队尾，从队头处理，保证公平和服务顺序。栈是后进先出，不符合这要求。”

**核心点 (Key Points):**
* FIFO (先进先出)
* Relate to scenario: tickets processed in order received (关联场景：工单按接收顺序处理)
* Contrast with Stack (对比栈)

---

## 2. BST的对数搜索时间 (BST Logarithmic Search)

**Q: Explain how binary search trees support logarithmic search times.**
**问：解释二叉搜索树如何支持对数搜索时间。**

* **EN (学生式答案):** "BSTs are **ordered**. When searching, you compare with the current node: go left if smaller, right if larger. In a balanced tree, this **cuts the search area roughly in half** each time. So, even with many nodes, searching is fast, related to the logarithm of the node count."
* **中文 (学生式答案):** “二叉搜索树能实现对数搜索时间，主要是因为它**有序**。每次查找时，和当前节点比较：小了就往左，大了就往右。理想情况下（树比较平衡），每比较一次，搜索范围就**大约减半**。所以节点再多也快，查找次数和节点数的对数差不多。”

**核心点 (Key Points):**
* Ordered property (有序性)
* Comparison leads to halving search space (in a balanced tree) (比较导致搜索空间减半 - 在平衡树中)
* Logarithmic relationship (对数关系)

---

## 3. 递归方法的三个要求 (Requirements for Recursion)

**Q: List and explain the three requirements for a properly designed recursive method.**
**问：列出并解释正确设计的递归方法必须满足的三个要求。**

* **EN (学生式答案):** "A good recursive method needs three things:
    1.  **A 'time to stop' (Base Case):** Solves a small enough problem directly without calling itself, to avoid an infinite loop.
    2.  **Problem must get smaller (Recursive Step/Reduction):** Each self-call must tackle a simpler version of the problem, moving closer to the base case.
    3.  **Actually call itself (Recursive Call):** Use the same method to solve that smaller problem."
* **中文 (学生式答案):** “一个好的递归方法需要三样东西：
    1.  **要有‘停下来’的时候 (基本情况):** 问题小到可以直接解决，不再调用自己，不然就没完没了。
    2.  **问题要能变小 (递归步骤/问题规模缩小):** 每次调用自己，交给自己解决的问题要比当前问题更简单、更接近‘停下来’的情况。
    3.  **要真的调用自己 (递归调用):** 用同样的方法去解决那个变小了的问题。”

**核心点 (Key Points):**
* Base Case (to stop) (基本情况 - 用于停止)
* Recursive Step (problem gets smaller, approaches base case) (递归步骤 - 问题变小，趋向基本情况)
* Recursive Call (calls itself) (递归调用 - 调用自身)

---

## 4. 数据结构对比：数组 vs. 链表 (Arrays vs. Linked Lists)

**Q: Compare and contrast arrays and linked lists in terms of insertion/deletion and access time.**
**问：比较和对比数组和链表在插入/删除和访问时间方面的特点。**

* **EN (学生式答案):** "Arrays are fast for **accessing** elements (direct index, $O(1)$), but slow for **inserting/deleting** in the middle ($O(n)$) because elements need to shift. Linked lists are slow for access ($O(n)$, must traverse), but faster for **inserting/deleting** once the position is found ($O(1)$ by changing pointers). Linked lists are also flexible in size."
* **中文 (学生式答案):** “数组**查（访问）**东西快（直接用下标，$O(1)$），但中间**插/删**东西慢（$O(n)$），因为后面的都要动。链表查东西慢（$O(n)$，得一个个找），但在找到位置后插/删都快（$O(1)$，改几个指针就行）。链表大小也灵活。”

**核心点 (Key Points):**
* Array: Fast access, slow middle insert/delete. (数组：访问快，中间插入/删除慢)
* Linked List: Slow access, fast insert/delete (at known position). Flexible size. (链表：访问慢，（已知位置）插入/删除快。大小灵活)


---

## 5. BST平衡的目的 (Purpose of Balancing BST)

**Q: What is the purpose of balancing a binary search tree (e.g., in AVL trees)?**
**问：平衡二叉搜索树（例如AVL树）的目的是什么？**

* **EN (学生式答案):** "Balancing a BST (like an AVL tree) is to **prevent it from becoming skewed** (like a linked list). If it's skewed, search becomes slow ($O(n)$). Balancing keeps the tree's height low (around $O(\log n)$), so searches stay fast at $O(\log n)$."
* **中文 (学生式答案):** “平衡BST（像AVL树）是为了**防止它长歪**（变得像链表）。如果树歪了，查东西会很慢（$O(n)$）。平衡能保证树的高度总是比较低（大约 $O(\log n)$），这样查东西就能一直很快，保持 $O(\log n)$ 的效率。”

**核心点 (Key Points):**
* Prevent skewed tree / linked list worst-case. (防止树倾斜/链表化)
* Maintain low height ($O(\log n)$). (保持较低的高度)
* Ensure $O(\log n)$ performance for operations. (确保操作的 $O(\log n)$ 性能)

