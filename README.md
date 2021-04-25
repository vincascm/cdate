
[中文](README.md) | [English](README_EN.md)


### 编写初衷

公历转农历、万年历之类的程序很多，linux系统下也能找到许多，但都不太中意，要么功能不全，要么体积臃肿，于是自己动手#&!.

### 农历小知识

农历是相对公历而言，指中国传统的历法，中国数千年来历法非常多，实用化的也有上百种，现在用的农历是明崇祯时制定、清顺治时开始使用的一种历法。

这种历法同样是一种阴阳历，月份按月亮的公转确定，节气由地球的公转确定。

### 借鉴与版权

算法是网上广为流传的一个版本，也是从代码的空间和时间上看目前较优的一种，主要参考了Javascript和Java两个版的写法。

先写了个bash shell的，发现让shell干带点儿计算量的活有点屈才，就用C重写了。虽然算法一样，但在一些地方做了修改，需要shell版的话可以去我的空间找。

这种算法本质上是查表算法，缺乏灵活性，也不够强大，根本的算法是天文历法的计算方法，可以参见寿星万年历的实现，可以显示数千年公历、农历的各种信息。

### 算法说明

用一个数组储存了1900-2050年农历每年是否有闰月及闰月、每月的大小，当前的年月日与1900年相差有多少天，根据这个相差的天数减去从1900年开始农历每年的天数，最终推算出当天农历的年月日。

节气的计算涉及很多天文学知识，计算也比较繁复，用一个数组储存了预计算值，精确到分，再根据公历月份计算出节气的具体日期，四柱的月柱由节来确定（一个公历月有两个节气，前一个为节，后一个为气），所以根据节气修正月柱。年柱由立春确定。

### 源代码说明

C语言版的分两部分，算法由 `chinese_calender.h` 提供，由 `chinese_calender` 传出农历数据，它返回一个`c_calender` 的结构，调用方法及结构说明都在`chinese_calender.h` 里了。

该算法不调用任何外部函数及C库函数，方便不同语言、不同架构的移植。`cdate.c` 调用 `chinese_calender` 取得农历数据，然后根据这些数据显示中文农历日历、节日、四柱。若要改变文字编码，只需将cdate.c文件的编码格式由UTF-8改为其它需要的格式。

### 反馈交流：

我的博客: <https://www.vinoca.org>

