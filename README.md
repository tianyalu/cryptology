# 密码学

[TOC]

## 一、密码学开端

### 1.1 推荐做的3件事

* 汤姆·汉克斯主演的《达芬奇密码》《但丁密码》,尼古拉斯·凯奇《国家宝藏》

* 蝉3301全球招聘（2012年)

  [https://www.bilibili.com/video/BV1ch411X7cg/?spm_id_from=333.788.videocard.O](https://www.bilibili.com/video/BV1ch411X7cg/?spm_id_from=333.788.videocard.O)

  [https://mp.weixin.qq.com/s/c7mhOyQmkOfBwJ_SkBPjmA](https://mp.weixin.qq.com/s/c7mhOyQmkOfBwJ_SkBPjmA)

* 关于列奥纳多·达·芬奇

  [https://www.bilibili.com/video/BV197411H7XX?from=search&seid=212482397985612139&spmLid_.from=333.337.0.0](https://www.bilibili.com/video/BV197411H7XX?from=search&seid=212482397985612139&spmLid_.from=333.337.0.0)

### 1.2 符号密码

从古代的岩壁画、泥印到近代的书籍、宗教的特殊符号，都是一种密码费斯托圆盘(无人破解)、伏尼契手稿(无人读懂)

[https://www.ancient-symbols.com/chinese/symbols_by_subjects.html](https://www.ancient-symbols.com/chinese/symbols_by_subjects.html)

### 1.3 隐写术简介

* 封蜡技术、隐形墨水、吞服信条等中国也有记载，不过最早出现在希腊
* 酸碱型、沉淀型、络离子型、氧化还原型及催化型等古代中国人，将密信写在丝绸上，用蜡封起来吞到肚子里

### 1.4 卡登格子隐藏法

意大利数学家卡登：

* 事先准备两张卡片，重叠后同时打穿N个洞孔，得到两张完全相同的带洞孔的卡片
* A方传递信息时，将卡片盖在白纸上，在洞孔内写入明文
* 然后拿开卡片后，编写一段看似无意义的文字将明文随机混在文字中
* B方解密时，同样将卡片盖在文字上，从洞孔中得到A方传递的明文

## 二、古典密码

### 2.1 密码学基石

* 置换密码：即明文字母保持不变，顺序被打乱；
* 替换密码：明文字母被替换，顺序保持不变。

### 2.2 置换密码

#### 2.2.1 滚筒密码

置换原理：

* 将两根直径相同的木棍分发给A、B两方；
* A需要传达保密信息时，用条状纸条在木棍上绕圈卷满；
* 然后垂直方向写下明文，最后将条状纸条松开后，形成密文；
* 即便信件被俘虏或者叛变，没有对应直径的木棍是无法还原明文的。

### 2.3 替换密码

#### 2.3.1 凯撒密码（表单替换）

错位方法，第4个字母代替第1个字母，例如：A -> D、X -> A (偏移3位)，借鉴这种思想，这个偏移位变量可以是任意数值。

* 优点：加密公式简单、解密容易理解；
* 缺点：容易被**穷举法** 破解。

![image-20220309195223458](https://gitee.com/tianyalusty/pic-go-repository/raw/master/img/202203091952576.png)

* 明文：`simon`
* 密文：`BAABAABAAAABBAAABBBAABBAB`

![image-20220309195641955](https://gitee.com/tianyalusty/pic-go-repository/raw/master/img/202203091956016.png)

#### 2.3.2 维吉尼亚密码（多表替换）

为了提高单表替换破译的难度发明的，使用词组作为秘钥，词组中每一个字母作为索引来确定采用的替换表。

* 明文：`android 2 java`
* 秘钥：`simon`
* 密文：`svpfbal 2 vois`

加密说明：

* 明文 A 行，对应秘钥 S 列，得到密文：S
* 明文 N 行，对应秘钥 I 列，得到密文： V
* 明文 D 行， 对应秘钥 M 列， 得到密文： P
* 秘钥结束后循环使用

解密说明：

* 秘钥 S 行，找到密文 S，得到列为： A
* 秘钥 I 行，找到密文 V，得到列为： N
* 秘钥 M 行，找到密文 P，得到列：D
* 秘钥结束后循环使用

![image-20220309195924152](https://gitee.com/tianyalusty/pic-go-repository/raw/master/img/202203091959258.png)

明文：`Android and Java are good friends`

密文：`Svpfbal mbq Biho njm scbv ndwrfle`

破译者很容易分析出秘钥的长度和内容（比较同一字母比如`a`出现的密文）

* 优点：相对复杂的秘钥，同一字母、不同秘钥可以加密出不同的结果；
* 缺点：加密内容如果足够长，则会出现大量重复的密文序列。

## 三、古代银票密码

### 3.1 河图洛书

中国的河图洛书，两幅神秘图案，被誉为“宇宙魔方”，是中华文化、阴阳五行术数之源。

“河出图，洛出书”，河，黄河；洛，洛水。

### 3.2 藏头/尾诗

类似字谜、灯谜都属于典型的密码、用来隐藏、传递信息。

藏头诗：

```
项伯胡为赐姓刘
目前更看牧羊人
实时新月落江城
战陈无勇非孝也
```

藏尾诗：

```
位分南北与东西
知谁肯访席为门
小溪过了到招提
不待子规相劝督
```

### 3.3 倒序密码

正、反读，意义截然不同，所以，加密中有：字段、逐字倒序（单词、字母）

![image-20220309202936107](https://gitee.com/tianyalusty/pic-go-repository/raw/master/img/202203092029154.png)

### 3.4 日升昌银票

现今仅存一张汇票，也只是店中伙计无意放入口袋中忘记销毁才“幸免于难”。从纸张、水印、印章、密码到书法，古人在小小汇票上层层加设了五道关卡，运用智慧，实现了汇票的有效防伪。

![image-20220309203205938](https://gitee.com/tianyalusty/pic-go-repository/raw/master/img/202203092032132.png)

#### 3.4.1 密码-月份

谨防假票冒取，勿忘细视书章

> 这12个字分别代表了1-12个月

#### 3.4.2 密码-日期

堪笑世情薄,天道最公平。昧心图自私,阴谋害他人。善恶终有报，到头必分明。

> 共30个字，其实表示的一个月的1号至30号

#### 3.4.3 密码-计量

坐客多察看，斟酌而后行

> 这10个字分别表示的是银两计数中的1至10

#### 3.4.4 密码-单位

国宝流通

> 分别表示**万**、**千**、**百** 和 **两**四个计数单位

#### 3.4.5 举例

1月9日汇银5000两（鉴别人很容易识别）

在不更换 **秘钥** 的前提下，正确方式是：**谨公看宝通**

## 四、达芬奇密码

### 4.1 达芬奇简介

如果说特斯拉是最接近神的男人，那达芬奇就是神他是人类历史上绝无仅有的全才，留下了不多的名画、达芬奇手稿，涉及各个领域，机械研究、武器设计、人体解剖、绘画、雕刻、发明、建筑设计，数学生物学、物理学、天文学、地质学、城市规划等学科。保存下来的手稿大约有6000页。

虽说都有文字注释，但用到了独特的加密方法，镜像书写法.

https://www.bilibili.com/video/BV197411H7XX?from=search&seid=212482397985612139&spm_id_from=333.337.0.0

### 4.2 达芬奇密码筒

* 将草质信纸、醋同时放入密码筒中；一旦被暴力破解，信纸将被醋溶解，密码将得以保存；
* 5个转轮，每个转轮26个字母组成，密码虽然只有5位，却有26的5次方，1180多万的可能；已经接近近代的机械密码了

![image-20220310201526887](https://gitee.com/tianyalusty/pic-go-repository/raw/master/img/202203102015007.png)

## 五、机械密码

### 5.1 电报

一战期间，用广播传送情报的方式被发现非常容易被窃听，所以密码技术在这期间得到了极大的应用与发展。

尤其在1917年 **齐默尔曼电报** 被破译直接导致了没过参战。

### 5.2 摩斯密码（滴答声）

![image-20220310202030688](https://gitee.com/tianyalusty/pic-go-repository/raw/master/img/202203102020804.png)

![image-20220310202446436](https://gitee.com/tianyalusty/pic-go-repository/raw/master/img/202203102024551.png)

### 5.3 `Enigma`密码机

* 二战时期，德国太过依赖和相信`Enigma`密码机；
* `Enigma`的破解 **提前结束了二战** ，最终德国战败告终。

![image-20220310202644696](https://gitee.com/tianyalusty/pic-go-repository/raw/master/img/202203102026783.png)

### 5.4 九七式紫色密码机

二战时期，日本人使用的密码机

* 1938年 中国戴笠将军（军统特务头子）聘请的前美国军情八处雅德利于当年2月首次破译成功；
* 1940年 美国中情局就已经破解了该密码；
* 1941年 日本偷袭珍珠港，使得美国将原子弹的研制计划提上日程；
* 1942年 中途岛海战，美国大胜日本，密码的重要性不言而喻；
* 二战末期的1945年8月6日和9日，美军对日本广岛和长崎投掷原子弹造成大量平民和军人伤亡。

![image-20220310203244958](https://gitee.com/tianyalusty/pic-go-repository/raw/master/img/202203102032119.png)

### 5.5 `Sigaba`密码机

从未被破解的密码机：`Sigaba`

* 采用更为复杂的机械运动使`Sigaba`密码更像是随机产生的；
* 也是二战期间唯一没有被破解的密码装置。

## 六、现代密码

### 6.1 单钥、公钥术语

* 单钥/对称（传统密码体制）：**加密** 和 **解密** 过程中，使用的是 **同一个秘钥**；
* 公钥/双钥/非对称：秘钥对（公、私钥），私钥可以生成公钥，一把加密另一把解密。

单钥图解：

![image-20220311191940950](https://gitee.com/tianyalusty/pic-go-repository/raw/master/img/202203111919076.png)

公钥图解：

![image-20220311192019162](https://gitee.com/tianyalusty/pic-go-repository/raw/master/img/202203111920333.png)

### 6.2 计算机的诞生

1946年，第一台计算机诞生。随着计算机的诞生，人类将告别手工、机械编码。诞生中间的二十多年时间里，密码学几乎停滞前行，直到上世纪70年代，发生了两件重大的事情，进入了现代密码。

#### 6.2.1 大事件一

`DES`(单钥/对称)

* 1972年 美国`IBM`公司研制的 **对称密码体制** 加密算法；
* 1976年 美国对全球公布了数据加密算法：`DES`；
* `DES`的原始思想可以参考二战德国的`Enigma`密码机，其基本思想大致相同，进行了扩散模糊、或者说替代模糊，增加了分析的难度。

#### 6.2.2 大事件二

`RSA`(公钥/非对称)

* 1977年 三位数学家`Rivest`、`Shamir`和`Adleman`设计了非对称加密算法；
* 命名 这种算法用他们三个人的名字命名，叫做 **`RSA`算法** ；
* 迄今为止，**`RSA`算法** 一直是最广为使用的 “非对称加密算法”，毫不夸张的说，只要有计算机网络的地方，就有 **`RSA`算法** 。

## 七、对称密码

### 7.1 `Shannon`设计思想

上世纪70年代，美国公布了数据加密标准算法：`DES`（对称加密）

* 扩散，将明文尽可能的散步到较长的密文中（置换思想）；
* 混淆，将明文、密文、秘钥之间的关系、规律等混淆化（代换/替换思想）。

### 7.2 不安全的`DES`

`DES`加密被破解：

* 1997年6月，美国某程序员经过3个月宣布破解；
* 2008年，某公司将`DES`暴力破解缩短到1天之内。

### 7.3 `3DES`

`Triple DES`，三重数据加密算法：

`AES`出现前，针对`DES`改进、强化。`3DES`又叫`Triple DES`，是三重数据加密算法，相当于是对每个数据块应用 **三次`DES`** 加密算法。

* 优点：`DESede`算法针对其秘钥长度偏短和迭代次数偏少等问题做了相应改进，提高了安全强度；
* 缺点：`DESede`算法处理速度较慢，秘钥计算时间较长，加密效率不高等问题。

### 7.4 `IDEA`

`IDES`(`International Data Encryption Algorithm`，国际数据加密标准)

华人：来学嘉，国际著名密码学专家、`IDEA`密码的发明者；瑞士籍华人，是中国和瑞士联合培养的 **国际级密码学家**，`IDEA`曾经也是`AES`算法标准的 **主要竞争者** ,其安全性已经在国际密码年会上被证明。

* 从理论上讲，至今还没有出现对该算法的有效攻击算法；
* 以目前计算机水平，破译一个`IDEA`秘钥至少需要1013年；
* 目前较为常用的电子邮件加密算法之一。

### 7.5 `AES`

`AES`(`Advanced Encryption Standard`，高级数据加密标准)

* 美国联邦政府用来替代`DES`的加密标准；
* 从1997~2000年，美国国家标准技术局向全球征集`AES`算法，最终采用了`Rijindael`算法。不过搞笑的是核心算法并不是数学家设计的，而是比利时两个搞工程学的大佬创作的；
* 能够有效抵御已知的针对`DES`算法的所有攻击方法，如部分差分攻击、相关秘钥攻击等；
* `AES`算法具有 **秘钥创建时间短、灵敏性好、内存需求低** 等优点；
* 除了常用的`SSH`软件外，在一些 **无线路由器** 中也使用`AES`算法构建加密协议。

### 7.6 加密算法

主要分为：分组、填充、迭代。

* 分组：明文特别长，加密的效率就非常重要了，要提高效率，则需要并行计算，就需要对明文划分成相同的长度，这个过程就叫做分组；
* 填充：由于要划分成相同长度才好实现统一的加密解密处理，那么久必然会出现分组最后的那一组字符串出现长度不够的问题，因此需要把缺失的长度补充上去，这个过程称之为填充；
* 迭代：简单的一次加密计算，必然是很容易被破解的，所以要增加算法的安全性，就需要对明文的计算转换进行多次，吧每一次的计算称之为迭代。

### 7.7 迭代模式

`ECB`、`CBC`等迭代模式：

轮秘钥加，字节代换，行移位，列移位，列混淆，异或，模，模加，移位，与，或，非运算等，将上述方案通过规律的组合后形成了迭代模式，也就是`ECB`、`CBC`等。

## 八、非对称密码

### 8.1 非对称密码的短板

秘钥只有一把，如何安全的分发是最大的问题。

### 8.2 非对称：`RSA`

*  1976年，密码学家与安全技术专家`Diffie`与`Hellman`提出 **公钥密码思想**；
* 1977年，数学家`Rivest`、`Shamir`和`Adleman`在麻省理工学院工作时设计了非对称加密算法；
* 设计思想：**大整数分解**（既可以加密，也可以签名）；
* 三位数学家`Rivest`、`Shamir`和`Adleman`，其中伯克利分校博士毕业的`Adleman`是计算机病毒的教父，也是`DNA`计算的创始人。

### 8.3 大整数分解

将一个正整数分解为几个质数之乘积：

* 45 = 1 * 3 * 3 * 5；看似简单，却是数学难题，想象一个无穷大的正整数如何分解；
* `Mips`年：每秒处理100万次指令计算，所需要的年份；
* 理论上破解1024位`RSA`需要3000亿`mips`年，实际上不到2年，所以现在用2048位；
* 2019年谷歌对外宣布量子计算机8小时破解2048位`RSA`；
* 所以我们迫切需要研发抗量子计算的密码体制。

### 8.4 `RSA`缺点

加密速度非常慢：

* 理论上比对称加密慢1000倍，实际上慢20倍以上；
* 所以，`HTTPS`请求时，**`SSL`证书** 使用 **`RSA`校验** ，后续数据使用`AES`加解密；
* 人类需要研发更快的非对称体制。

### 8.5 `ECC`椭圆曲线

椭圆曲线密码学（`Elliptic curve cryptography`，缩写为`ECC`）

* 针对`RSA`加密速度慢，`ECC`椭圆曲线密码体制应用而生；
* 1985年，由`Neal Koblitz`和`Victor Miller`分别独立提出的；
* 2005年2月，美国国家安全局宣布采用`ECC`作为美国联邦政府 **加密标准之一**；
* 椭圆曲线并不是椭圆，因为方程与计算椭圆周长的方程相似，都是用三次方程来表示；
* 设计思想：**求离散对数**，也就是循环群子群问题；

* 优势：使用更短的秘钥来获得相同水平的安全强度，从而使计算量大大减少；
* `ECC`(600`bit`长度)秘钥 = `RSA`(21000`bit`长度)秘钥（同`mips`年）。

### 8.6 总结

| 单钥/对称密码体系          | 公钥/非对称密码体系          |
| -------------------------- | ---------------------------- |
| 加密速度快，秘钥短         | 运算速度慢，秘钥长           |
| 秘钥管理困（分发、更换）   | 秘钥管理简单（保管私钥）     |
| 不能实现身份认证、数字签名 | 实现了用户身份认证、数字签名 |

* 加解密类型分为：对称、非对称；
* 加解密结果分为：可逆、不可逆；
* 加解密用的同一秘钥（私钥），加对称加密；
* 加解密用了两把秘钥（公钥、私钥），叫非对称加密。

## 九、深入`RSA`、`ECC`

### 9.1 签名与验签

不可篡改性、不可抵赖性：

* 服务端，使用 **私钥** 对 **源数据/摘要** 进行 **不可逆签名** （生成 **校验值**）；
* 服务端，将 **公钥、源数据、摘要、签名（校验值）** 一起发给客户端；
* 客户端，使用 **公钥** 对 **源数据/摘要**  和 **签名（校验值）** 进行 **验签** ；
* 验签通过，则表示服务端数据 **未被篡改** ；
* 数字证书，国际 **`CA`认证机构** ，颁发的 **授权证书** ，将服务端的 **公钥进行绑定** ；
* 验签通过，则表示服务端数据 **不可抵赖** 。

## 十、消息摘要

### 10.1 消息摘要的概念

对 **特定的数据** 进行 **不可逆** 的 **数据摘要** ，生成一段 **唯一** 的 **校验码** 用来 **判断** 数据 **是否被篡改** 。常见的有`MD5`、`SHA`等。

### 10.2 消息摘要的由来

* 任意长度的消息/文件压缩到某一固定的长度；
* 具有不可篡改性、不可逆转性；
* 频繁的数据交互，比非对称的 “签名、验签”更快。

### 10.3 `Hash`

`Hash`，一般翻译做“散列”，直接音译为“哈希”，也叫做“杂凑函数”，简单的说就是一种将 **任意长度** 的 **消息/文件** 压缩到某一 **固定长度** 的消息摘要的 **函数**。

### 10.4 `MD5`、`SHA`

* `MD5(Message Digest Algorithm 5)`，消息摘要算法第五版；
* `SHA(Secure Hash Algorithm)`，安全散列算法。

比较：

二者均由`MD4`导出，`SHA-1`和`MD5`彼此很相似

> 1. `MD4`: 1990年设计，适用在32位处理器；
> 2. 抗攻击性：`SHA-1`摘要比`MD5`长32位；
> 3. 抗分析性：`SHA-1`大于`MD5`;
> 4. 运行速度：`SHA-1`慢于`MD5`.
>
> 

`MD5`是`Rivest`与1991年对`MD4`的改进版本

> 1. 目前适用最广泛的`Hash`算法；
> 2. 加密后不可逆（不能反推出原生信息/文件）；
> 3. 抗碰撞性，试图寻找两个不同输入得到相同的输出值是不现实的；
> 4. 文件完整性校验、消息完整性校验（具有不可篡改性，常用于数字签名）；
> 5. 具有高度的离散性。

### 10.5 `MD5`用途

* 只能用于 **信息验证**， 而不能用来 **加密解密** 进行消息传递；
* 通常用于 **密码的加密存储，数字签名，文件完整性验证** 等；
* 针对安装程序的 **唯一校验码** （办公软件`MD5`、开发工具`SHA`）。

### 10.6 对摘要进行数字签名

`Hash`算法也是 **现代密码体系** 中的一个 **重要组成部分**；

由于 **非对称算法** 的运算速度 **较慢** ， 所以在数字签名协议中，**单向散列函数** 肩负重任，对`Hash`值，又称“数字摘要”进行数字签名（非对称）。

### 10.7 `SHA`系列

`SHA-224`、`SHA-256`、`SHA-384`、`SHA-512`统称为`SHA2`加密算法：

* `SHA-1`是由 美国标准技术局（`NIST`)颁布的国家标准，被政府部门和私营业主用来处理敏感的信息；
* `SHA2`加密算法比`SHA1`高，`SHA-1`基于`MD5`,`MD5`又基于`MD4`。

### 10.8 彩虹表

攻击者创建了一个叫 **彩虹表** 的东西：

* 它是非常庞大的 **数据库** ，收集了所有 **常用的密码**，以及这些密码对应的`MD5值`、`SHA-1`值等；
* 主流的彩虹表记录数据约为 **90万亿条** ，占用硬盘超过 **`500TB`**;
* 可以通过 **穷举法** 反向查询出`MD5`值、`SHA-1`值等对应的 **原文**；
* 如果很不幸被收集在彩虹表里，就可能被 **破解掉**。

### 10.9 被国人破译

中国数学家：王小云。

2005年8月，王小云、姚期智、姚储枫等人破译美国两大安全密码：`MD5`、`SHA-`，研发国密：`SM3`(`SHA-256`基础上改进实现的一种算法)

### 10.10 摘要组合计算（混合密码）

为了增加破译的难度：

* `MD5(SHA1)`、`MD5(SHA256)`、`MD5(SHA384)`、`MD5(SHA512)`混合
* `MD5(SHA1)`、`MD5(SHA256)`、`MD5(SHA384)`、`MD5(SHA512)`混合
* .` HMAC(MD5)`、`HMAC(SHA1)`、`HMAC(SHA256)`、`HMAC(SHA384)`、`HMAC(SHA512)`混合

## 十一、消息认证码

### 11.1 问题思考

数据和`MD5`同时被篡改的问题：

如果第三方修改了数据，然后进行`MD5`散列，并一起发送给接收方，接收方并不能察觉到数据被篡改。

### 11.2 `HMAC`概念

`HMAC(Hash Message Authentication Code)`，散列/哈希消息认证码

* 1996-1997年，散列消息认证码（带 **秘钥** 的 `Hash`函数，**不属于对称密码**）；
* 密码学中，**通讯双方** 使用的一种 **验证机制** ，保证消息数据 **完整性**；
* 与 **消息摘要** 最大的不同就是有 **签名秘钥** ，常用于身份认证中。

### 11.3 场景分析

消息认证码是基于 **消息** 和 **秘钥** 生成的 **消息摘要** ，可以与任何 **迭代散列函数** 绑定使用。

> 一般都是 **服务器** 与 **服务器** 数据交互的时候做数字签名，**前端（含移动端）** 与 **服务器** 交互，一般搜索拿 **机器码**、**设备号** 作为 **秘钥** ，事先约定好的 **秘钥** ，第三方无法计算后续数据正确的散列值，以此来 **防止数据被篡改** 。

流程：

* 客户端向服务器发送一个验证请求（比如：注册/登录）；
* 服务器接到此请求后生成一个**随机数** 传给 **客户端**；
* 客户端将收到的随机数与`HMAC`秘钥（设备、机器码）进行`HMAC-MD5`运算，并将得到的结果作为认证传给服务器；
* 服务器也使用该随机数与`HMAC`秘钥（数据库字段）进行`HMAC-MD5`运算；
* 如果服务器的运算结果与客户端传回的响应结果相同，则认为客户端是一个合法用户（此方法也可以用作服务器与服务器之间的身份认证）。

### 11.4 `SSL`握手

* `A`生成一个 **随机数** 向`B`发出一个验证请求；
* `B`收到请求后生成另一个 **随机数** ，并发送自己的 **数字证书** ，包含 **认证信息** 及**公钥** ；
* `A`通过 **`CA`证书** 验证有效性，生成另一个 **随机数**；
* `A`使用 **私钥加密** 随机数，使用`B`的 **公钥加密** 随机数后，将 **数字证书** 和 **加密结果** 发送给`B`；
* `B`通过  **`CA`证书** 验证有效性，使用 `A`的 **公钥解密** 第三个随机数；

* 基于前面提供的 **3组随机数** ，计算出用于 **数据对称加密** 的 **临时公共秘钥**，秘钥交换后，`A`和`B`通过 **数据加密** ，交换 **`HMAC`秘钥** ，作为后续的 **数字签名**。

### 11.5 总结

* 摘要算法，不能防止第三方篡改，也无法认证身份；
* 非对称做数字证书，不善于数据频繁加解密和验签；
* `CA(Certificate Authority)`数字证书认证中心，`PKCS10`数据包；
* `CA`数字证书、自签署证书（移动端不用、引入`Token`）。

## 十二、盐

彩虹表攻击、变型盐、密码机制

### 12.1 彩虹表攻击

* 被穷举：只对密码进行`MD5`、`SHA`系列加密很容易被穷举出来；
* 被攻击：无论数据库被内部攻击还是外部攻击；
* 被参考：当两个用户密码相同时，数据库保存着相同的密码。

### 12.2 思路

* 目标：哪怕用户 **密码一致** ，存储到数据库是 **不同的** 结果值；
* 方案：`MD5-SHA`用户密码（`MD5`/`SHA`) + 伪随机值；
* 结果：**增加安全系数** ，即使密码相同，存储到数据库的结果也不一样；
* 总结：上述 **伪随机值** 就是 **盐** ，好比做菜时，放入佐料（加盐）。

### 12.3 盐

盐本身就是一种规律、约定的消息，可以是 **字符串** ，也可以是某个不可变物理 **硬件的编号** ，比如`U`盘的自身 **唯一标识** ，移动端的手机 **识别码、唯一标识** ，电脑防篡改硬件的 **机器码** 等等。

#### 12.3.1 问题

* 存储：密码、盐值，都存储在数据库中，鸡蛋都放在一个篮子里；
* 泄漏：如何保证在数据完全泄漏的情况下保证用户密码安全；
* 思路：能不能设计一种伪盐，让攻击者无法得知真实盐；
* 方案：通过代码执行某种自定义算法，从假盐中提取出真盐。

#### 12.3.2 隐藏盐值

* 固定长度：盐值长度（如固定8~32位）；
* 规律拆分：将盐值逐字符拆分，有规律地插入到伪随机值中；
* 伪造伪盐：比如：['随机'，'盐'，'随机'，'随机'，'盐'，'随机'，'随机'，'盐'，'随机']；
* 伪盐长度：伪盐长度 = 真盐长度 * `N` （插入间隙比率）。

#### 12.3.3 场景

* 客户端：用户注册时，`MD5/SHA`对密码生成不可逆`hash`值；
* 生成盐：服务端对每个用户生成“唯一”盐值（伪随机）；
* 新散列：使用密码`hash`+盐值，再生成心动不可逆`hash`（新密码）；
* 伪造盐：通过自定义算法，将盐值转成假盐（伪盐、变盐）；
* 存字段：将新密码、假盐存储到数据库的两个字段中；
* 取真盐：用户登录时，从数据库取出假盐，通过自定义算法取出真盐；
* 校验值：`MD5-SHA`(用户密码<`MD5/SHA` + 真盐)，对比数据库存储密码；

## 十三、银行`U`盾

### 13.1 银行`U`盾常识

* 银行激活`U`盾：在购买了银行`U`盾之后，需要在本行激活；
* 银行设置密码：激活`U`盾后，才可以设置`U`盾密码；
* 每次输入口令：`U`盾插入电脑，每次都要输入口令，且不担心丢失。

### 13.2 设计思想

![image-20220323193035516](https://gitee.com/tianyalusty/pic-go-repository/raw/master/img/202203231930639.png)

## 十四、国密

### 14.1 `SM1`对称密码

* 软硬件实现性能与`AES`相当，**算法不公开** ，仅以`IP`核的形式存在于**芯片** 中；
* 采用该算法已经研制了 **系列芯片** 、智能`IC`卡，智能密码钥匙、加密卡、加密机等安全产品，广泛应用于 **电子政务、电子商务** 及 **国民经济** 的各个领域（包括 **国家政务通、警务通** 等重要领域）。

### 14.2 `SM2`椭圆曲线

`SM2`椭圆曲线公钥密码算法：该算方法由国家密码管理局于2010年12月17日发布。

* 应用：加解密、签名；
* 算法：`ECC`椭圆曲线。

### 14.3 `SM3`摘要

`SM3`密码摘要算法：中国国家密码管理局2010年公布的 **中国商用** 密码杂凑算法标准，是在 `SHA0-256`基础上改进实现的一种算法。

### 14.4 `SM4`对称

`SM4`对称算法：多应用于 **无线局域网** 产品。

### 14.5 `SM7`对称

`SM7`对称密码：适用于非接触式`IC`卡，应用包括身份识别类应用（门禁卡、工作证、参赛证），票务类应用（大型赛事门票、展会门票），支付与通卡类应用（积分消费卡、校园一卡通、企业一卡通等）。

### 14.6 `SM9`标识

`SM9`标识密码算法，特点：适用方便，易于部署。

`SM9`算法不需要申请数字证书，云技术的密码服务、电子邮件安全、只能终端保护、物联网安全、与存储安全等数据加密、身份认证、通话加密、通道加密等安全应用。

### 14.7 `ZUC`祖冲之序列

**`ZUC`祖冲之序列密码** 算法是中国自主研究的 **流密码** 算法，运用于 **移动通信`4G`网络** 中的国际标准密码算法。

## 十五、量子计算机

### 15.1 量子

* 量子计算机：[https://baijiahao.baidu.com/s?id=1714699070293719539&wfr=spider&for=pc](https://baijiahao.baidu.com/s?id=1714699070293719539&wfr=spider&for=pc)
* 量子力学：[https://baijiahao.baidu.com/s?id=1719392473851799443&wfr=spider&for=pc](https://baijiahao.baidu.com/s?id=1719392473851799443&wfr=spider&for=pc)
* 量子霸权（降维打击）：[https://www.bilibili.com/video/BV1ME411E7U7?from=search&seid=7975951929973750778&spm_id_from=333.337.0.0](https://www.bilibili.com/video/BV1ME411E7U7?from=search&seid=7975951929973750778&spm_id_from=333.337.0.0)

### 15.2 量子计算机的发展

* 2007年，加拿大`D-Wave`全球首台16位量子计算机诞生;
* 2011年，加拿大`D-Wave`推出128位量子计算机;
* 2013年，`NASA`与`Google`预定512位`D-Wave Two`量子计算机

### 15.3 量子计算机的存储

|            | 单存储器     | 双存储器            | `N`存储器            |
  | ---------- | ------------ | ------------------- | -------------------- |
  | 传统存储器 | 单元存储0或1 | 00/01/10/11（任一） | 2的`N`次方中的一个数 |
  | 量子存储器 | 单元存储0和1 | 00/01/10/11（同时） | 同时存2的`N`次方个数 |

### 15.4 量子计算机强大的计算能力

* 强大的计算能力：比传统的计算机快千亿万亿倍；
* 例子：解决1000位的大整数分解问题，传统计算机需要10的25次方`mips`年，量子计算机只需要几分钟。

### 15.5 迫切研发

*   不难看出，传统密码学中的单钥/对称加密在量子计算机面前显得无能为力；
* 对公钥/非对称密钥搜索也是信手拈来；
* 2019年谷歌对外宣布量子计算机8小时破解2048位`RSA`；
* 针对`RSA`破解1024位，仅仅需要1秒(秀尔算法);
* 虽然还没有达到通用型计算机标准,但，我们迫切需要研发出抗量子计算的密码体制.

### 15.6 量子研发进展

* 1989年美国实现30公分量子密钥传输
* 1995年英国实现30公里量子密钥传输
* 1999年瑞典和日本实现40公里量子密钥传输
* 2002年德国、英国实现21公里量子密钥传输
* 2004年中国实现125公里量子密钥保密通信
* 2006年英国、荷兰实现21公里量子密钥传输
* 2008年瑞士、美国实现256公里量子密钥传输
* 2013年―中国首次实现了测量器件无关的量子密钥分发
* 2016年―世界首颗中国量子科学实验卫星“墨子号”升空

### 15.7 量子密码基础

* 方程：薛定谔方程；
* 观测：测不准原理；
* 克隆：不可克隆定理；
* 传闻：不可窃听、不可破译、决对安全的密码。

### 15.8 `DNA`密码

`DNA`计算机：随着 **`DNA`计算** 而出现的 **密码学新领域**，有高存储密度和高并行性的优点，一旦研发出生物计算机，**生物密码** 将随之而来。
