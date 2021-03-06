---
layout:         page
title:          "数据结构三要素"
date:           2020-06-03 21:00:00 +0800
width:          700
author:         zaofengchen
catalog:        true
permalink:      /:year/:month/:day/:title
tags:
    - blog
categories:     ['ds']
---

<!-- 渲染公式 -->
<script src="{{ site.url }}/static/js/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>
<script type="text/x-mathjax-config">
    MathJax.Hub.Config({
        tex2jax: {
        skipTags: ['script', 'noscript', 'style', 'textarea', 'pre'],
        inlineMath: [['$','$']]
        }
    });
</script>
<!-- 渲染公式 -->

### 数据结构三要素
包括：
- 数据的逻辑结构
- 数据的存储结构
- 数据的运算

#### 数据的逻辑结构
指数据节点之间的逻辑关系，是数据在用户面前呈现的形式。

数据节点之间按逻辑结构可分为：
- 线性结构
    - [线性表](/2020/06/05/linear-list)
    - [栈](/2020/06/08/stack)
    - [队列](/2020/06/10/queue)
    - [串](/2020/06/17/string)
- 非线性结构
    - [树](/2020/07/11/btree)
    - 图

>线性结构的特点：
>- 数据节点之间只存在一对一的关系
>- 开始节点和终端节点都是唯一的
>- 除了开始节点和终端节点以外，其余节点都有且仅有一个前驱节点，有且仅有一个后继节点

>树形结构的特点：
>- 数据节点之间存在一对多的关系
>- 开始节点唯一，终端节点不唯一
>- 除了终端节点以外，每个节点有一个或多个后继节点
>- 除开始节点以外，每个节点有且仅有一个前驱节点

>图形结构的特点：
>- 数据节点之间存在多对多的关系
>- 没有开始节点和终端节点，所有节点都可能有多个前驱节点和多个后继节点

#### 数据的存储结构
指数据节点及其关系在计算机存储器中的存储方式，也称为数据的物理结构。

数据节点按存储结构可分为：
- 顺序结构：利用数组实现，空间利用率高
- 链式结构：利用指针实现，便于增删调整修改
- 索引结构：利用索引项实现，索引项包括关键字和地址，查找速度快，但是存储索引项会增加空间支出
- 散列结构：利用哈希公式等计算并存储数值为地址，作为快速查找的依据，但是缺点是存储数值会占用大量空间，并且仅保存数据数值，不保存数据的逻辑关系

#### 数据的运算
施加在数据上的运算包括运算的定义和实现。

- **运算的定义**针对逻辑结构，指出运算的功能；

- **运算的实现**针对存储结构，指出运算的具体操作步骤。

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gffjzcrz6kj30k80kcjrm.jpg" alt="数据结构" width="{{ page.width}}" align="bottom" />
<center>数据结构</center>

### 逻辑结构二元组
逻辑结构二元组是是表示数据逻辑结构的抽象工具。

逻辑结构二元组只关心两个问题：
1. 数据是什么，包括：
    - 数据是什么类型，例如int、char、struct
    - 数据的数量
2. 数据之间是什么关系
    - 数据之间是相邻关系，使用括号(e1,e2)表示
    - 数据之间是先后关系，使用尖括号<e1,e2>表示

逻辑结构二元组表示方法：
$B=(D,R)$。

1. B是一种数据结构，由数据元素的集合D和D上二元关系的集合R所组成
2. $D=\{d_i|d_i \in ElemType,1<=i<=n,n>=0\}$，
数据元素的集合
3. $R=\{<r_{j-1},r_j>|1<=j<=m,m>=0\}$，
D上二元关系的集合


比如二元组示例：
```
B = （D，R）
D = {a，b，c，d，e，f，g，h，i，j}
R = {r}
r = { <a，b>，<a，c>，<a，d>，<b，e>，<c，f>，<c，g>，<d，h>，<d，i>，<d，j> }
```
从它的二元关系的序偶 <a,b> 中可以看出这是一个有向关系，那么其二元组关系对应的逻辑结构如下图所示：

<img src="https://tva1.sinaimg.cn/large/007S8ZIlgy1gfk5mc4yk8j309d051jr6.jpg" alt="数据结构二元组示例" align="bottom" />
<center>数据结构二元组示例</center>


### 抽象数据类型(ADT)
抽象数据类型只关心数据节点的逻辑结构和抽象运算（即运算的定义），暂不考虑计算机的具体存储结构和运算的具体实现。实质上就是在用抽象的方法描述问题本身，目的是在不涉及具体的，和计算机系统相关的细节情况下，优先理解问题本身，在此基础上，实现用计算机求解问题的过程。

```
ADT <抽象数据类型>
{
    数据对象：<数据对象的定义>
    数据关系：<数据关系定义>
    基本操作：<基本操作定义>
}
```

对数据对象的定义和描述数据元素之间的关系，这个就是逻辑结构二元组的内容，所以，抽象数据类型就是逻辑结构二元组的扩展，在逻辑结构二元组的基础上增加对数据元素的基本运算定义。

线性表的抽象数据类型：
```
ADT List
{
数据对象：
    D = {ai | ai ∈ ElemType, i=1,2,…,n, n>=0 }              // ElemType为类型标识符int的别名
数据关系：
    R = {<ai-1, ai> | ai-1, ai ∈ D, i=2,3,…,n }
数据操作：
    （1）tabSeq * InitList();	                            // 初始化一个空的线性表，tabSeq为结构体类型
    （2）void CreateList(tabSeq *L, ElemType a[], int n);	// 创建线性表
    （3）Bool ListEmpty(tabSeq *L);	                        // 判断线性表是否为空
    （4）int ListLength(tabSeq *L);	                        // 返回线性表的长度
    （5）void DispList(tabSeq *L);	                        // 输出线性表元素
    （6）Bool GetElem(tabSeq *L,int i,ElemType *e);	        // 返回指定序号的元素
    （7）int LocateElem(tabSeq *L, ElemType e);	            // 返回指定元素的序号
    （8）Bool ListInsert(tabSeq *L,int i,ElemType e);	    // 在指定序号位置插入元素
    （9）Bool ListDelete(tabSeq *L,int i,ElemType *e);	    // 在指定序号位置删除元素
}
```

根据抽象数据类型的定义可以知道：
- 数据元素集合D包含n个int类型整数；
- R表示数据元素之间是有向的，具有前驱后继关系；
- 最后定义了9个基本运算，涵盖初始化，创建，判断是否为空……等等。

ADT可以帮助理解问题本身，理解对外暴露的接口，在次基础上，根据实际需求，选择合适的存储结构，实现具体运算。
