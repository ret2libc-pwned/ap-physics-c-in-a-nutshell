# AP Physics C in a Nutshell

Copyright 2025 [ret2libc-pwned@github](https://github.com/ret2libc-pwned/). Licensed under CC BY-NC-ND.

[TOC]

## Notations

本文中用粗体 $\renewcommand\vec{\boldsymbol}\vec{v}$ 表示单个字母的矢量 $\overrightarrow {v}$。 

为了方便输入，动能使用 $K$、势能使用 $U$ 表示。

## Mechanics

### 动力学中的物理量

位移 $\vec x$、速度 $\vec v$、加速度 $\vec a$：都是[矢量](###Vectors)；后者为前者对时间的导数。

**速率 (speed)** 是速度的大小 $|\vec v|$，为标量。

### 静力学  牛顿三定律

#### 牛顿第一定律

物体合外力 $\sum \vec F = 0 \Rightarrow $ 物体运动速度不变 (物体不改变运动状态)

#### 牛顿第二定律

$$
\vec a = \frac{\vec F}{m}
$$

牛顿第二定律声称，力是改变物体运动状态的原因。

#### 牛顿第三定律

$$
\vec F_{\text{AB}} = - \vec F_{\text{BA}}
$$

也就是说，相互作用的两个物体，作用力与反作用力的大小

- 等大
- 共线
- 反向

### 静力学与动力学常用结论

#### 匀加速直线运动

- $v(t) = v_0 + at$
- $\Delta x = v_0 t + \frac12 at^2$
- $v_t^2 - v_0^2 = 2a\Delta x$

对于从高度 $H$ 释放，**忽略空气阻力**的自由落体：

- $y(t) = H - \frac12 gt^2$
  - 落地所需时间 $t_\text{ground} = \sqrt{2H/g}$
  - 触及地面速度 $v_\max = \sqrt{2gH}$

对于垂直上抛运动：

- $y(t) = v_0t - \frac12gt^2$
  - 到达最高点的时间 $t_\text{highest} = v_0 / g$
  - 最高点的纵坐标 $y_\max = v_0^2 / 2g$
  - 对称性：到达初始高度的用时 $2t_\text{highest}$

斜抛运动 (运动的独立性)

- 水平方向上为匀速直线运动，竖直方向上为匀加速直线运动 (忽略空气阻力的情况下)。

- 写出参数方程
  $$
  \begin{cases}
  x(t) = (v_0\cos\theta) t\\
  y(t) = (v_0\sin\theta)t - \frac12 gt^2
  \end{cases}
  $$

- 运动的轨迹为抛物线

#### 圆周运动

先考虑匀速圆周运动的情况：质点的速度大小保持恒定，方向时刻改变。

考虑**极短时间** $\mathrm dt$ 内，质点从 A 点运动至 B 点，位移角 $\mathrm d\theta$。

取近似 $\mathrm dv \approx v\mathrm d\theta$ (通过几何关系，等腰三角形两腰为 $v$，顶角为 $\mathrm d\theta \to 0$，则速度差 $\mathrm dv = v\sin\mathrm d\theta \approx v\mathrm d\theta$，且 $\mathrm d\vec v$ 指向圆心)。
$$
\begin{aligned}
a = \frac{\mathrm dv}{\mathrm dt} &\approx \frac{v\mathrm d\theta}{\mathrm dt}\\
&= v\omega = \frac{v^2}{r} = \omega^2r
\end{aligned}
$$
对于非匀速的情况，通常把加速度分解成

- 切向加速度 $\vec a_\tau$ (转动加速度 $\vec\alpha$)
  - 改变速率的大小，不改变速度方向
- 法向加速度 $\vec a_r$ 
  - 时刻改变速度的方向

#### 阻力正比于速度的自由落体

> 物体在高处从静止状态释放，在空气中自由下落。我们认为空气阻力正比于物体下落的速度。求速度-时间函数。

- 首先，速度很小，空气阻力几乎不记。这个时候 $v \approx gt$ 近似线性增长。
- 随着 $v$ 增大，阻力 $kv$ 也增大，合力 $mg−kv$ 逐渐减小。这个时候 $v$ 增长的趋势开始减小。

考虑受力分析。物体受到

- 重力 $mg$
- 阻力 $f\propto v$

根据牛顿第二定律列出
$$
mg - kv = m\frac{\mathrm dv}{\mathrm dt}
$$
这是一个**一阶常微分方程**，分离变量求解
$$
\begin{aligned}
\frac{\mathrm dv}{\mathrm dt} &= g - \frac{kv}{m}\\
\Rightarrow \int \frac{\mathrm dv}{g - \frac{kv}{m}} &= \int \mathrm dt\\
\Rightarrow -\frac{k}{m}v + g &= C\exp\left(-\frac{kt}{m}\right)
\end{aligned}
$$
代入边界条件 $v(0) = 0$，解得 $C = g$。

因此
$$
\boxed{v(t) = \frac{mg}{k}\left(1 - \exp\left(-\frac{kt}{m}\right)\right)}
$$
计算 $v(t)$ 在 $t \to \infty$ 时的极限，有 
$$
v(t) \to \frac{mg}{k}
$$
称为**收尾速度 (terminal velocity)**。

速度函数如下图所示，TODO

<img src="https://files.oaiusercontent.com/file-Hrs2eXZZiWrwq34yFMYrGB?se=2025-05-03T07%3A17%3A46Z&sp=r&sv=2024-08-04&sr=b&rscc=max-age%3D299%2C%20immutable%2C%20private&rscd=attachment%3B%20filename%3Deb805f04-b375-48a4-9d39-16cd53946524&sig=1LSe0ia9eak9Dh4Llsm8q2no4anioLXq6iwodSOeC8Q%3D" alt="Output image" style="zoom:33%;" />

当阻力 $f \to 0$ 时，$k\to 0$，$\lim_\limits{t \to \infty} v(t) = gt$。

#### 行星轨道

万有引力
$$
F = G\frac{Mm}{r^2}
$$
引力势能
$$
U_\mathrm g = -G\frac{Mm}{r}
$$
开普勒三定律

1. 行星绕椭圆轨道运动，恒星位于一个焦点。
2. 行星与太阳的连线在相等的时间内扫过的面积相等。
3. $T = \sqrt{\frac{4\pi^2R^3}{MG}}$

### 做功、能量

能量是力在空间上的累积。

物体做功
$$
W := \int \vec F\cdot \mathrm d\vec x
$$

#### 动能

$$
K = \frac12 mv^2
$$

#### 保守力与势能

**保守力**做功与路径无关。(沿闭合回路，保守力做功为 $0$)

比如

- 重力
- 万有引力
- 电场力

保守力可以定义关于位置的势能函数 $U$。

**势能 $U$ 是储存于系统中的能量**，若保守力做正功，势能减小。
$$
U := -W_{A\to B} = U_B - U_A
$$
要求某点的势能，需要先定义势能零点。如电势能的势能零点被定义在无穷远处、重力势能的势能零点定义在 $h = 0$ 处。

#### 机械能守恒

封闭系统 (没有外界做功或能量损耗) 机械能守恒。
$$
(K + U)\bigl|_{\text{initial}} = (K + U)\bigl|_{\text{final}}
$$

#### 卫星轨道的能量

定义无穷远处为势能零点，计算万有引力的积分得到引力势能
$$
U_\text g = -\int_\infty^x G\frac{Mm}{r^2}\mathrm dr = \boxed{-G\frac{Mm}{r}}
$$

### 动量

定义物体的动量为 $\vec p = m\vec v$。

#### 动量定理

**冲量**为力在时间上的累积。
$$
I = \int F\mathrm dt = \Delta p, \quad \vec F = \frac{\mathrm d\bigl[\vec p(t)\bigr]}{\mathrm dt}
$$

#### 动量守恒

一个封闭系统满足动量守恒。如碰撞的过程中，虽然有能量损失，但是动量守恒。

### 转动

##### 角动量

$$
\vec L := \vec r \times \vec p
$$

展开得到 $|L| = mrv$。

对于刚体
$$
L = I\omega
$$

#### 转动惯量

$$
I := \int r^2 \mathrm dm
$$

##### 平行轴定理

距离转动轴 $d$ 平行轴作为新的转动轴，转动惯量增加 $Md^2$，其中 $M$ 为刚体质量。
$$
I^\prime = I + Md^2
$$

#### 线物理量与角物理量的转换

| **平动**              | **转动**                      |
| --------------------- | ----------------------------- |
| 位移 $x$              | 角位移 $\theta$               |
| 速度 $v$              | 角速度 $\omega$               |
| 加速度 $a$            | 角加速度 $\alpha$             |
| 质量 $m$              | 转动惯量 $I$                  |
| 力 $F$                | 力矩 $\tau$                   |
| 动量 $p = mv$         | 角动量 $L = I\omega$          |
| 牛顿第二定律 $F = ma$ | 转动牛顿定律 $\tau = I\alpha$ |

### 物体平衡条件

物体平衡 $\Leftrightarrow$ 物体合外力为 0 $\land$ 物体合外力矩为 0

所以在受力分析无法解决问题时别忘了分析力矩！

### 简谐振动

满足
$$
\frac{\mathrm d^2\vec x}{\mathrm dt^2} = -k\vec x\quad\text{(where $k$ is a positive constant)}
$$
的运动称为**简谐振动**。

根据振动函数 $x(t) = A\cos(\omega t)$，可知 $a(t) = -A\omega^2 x(t)$。

## EM

### 静电学

$$
\begin{matrix}
\text{库仑力 } F & \xrightarrow{} & \text{做功 } W & \xrightarrow{\quad} & \text{势能 } U \\
\downarrow&\quad&\downarrow&\quad&\downarrow\\
\text{场强 } E & \xrightarrow{\quad} & \text{电势差 } \Delta V & \xrightarrow{\quad} & \text{电势 } V
\end{matrix}
\quad
\begin{matrix}

\end{matrix}
$$

#### 库仑力

$$
\vec F = k\frac{q_1q_2}{r^2}\vec{\hat r}
$$

库仑力是[保守力](####保守力与势能)。

#### 场强

$$
\vec E = \frac{\vec F}{q} = k\frac{Q}{r^2}\vec{\hat r}
$$

场强是[电势](####电势)的负梯度。一维情况下，
$$
E = -\frac{\mathrm dV}{\mathrm dt}
$$

#### 势能

定义无穷远处电场势能为 $0$，某点的势能
$$
U(r) = -W_{\infty \to r} = k\frac{Q}{r}
$$
一个系统中，两个点电荷 $q_1,q_2$ 对势能 $U$ 的贡献为
$$
U(q_1, q_2) = k\frac{q_1q_2}{r_{12}}
$$

#### 电势

$$
V = \frac{U}{q}
$$

#### 电容

$$
C = \frac QV
$$

### 电路

基尔霍夫定律

- 基尔霍夫节点定律
- 基尔霍夫回路定律

$RC$ 电路

- 推导 
- 结论

### 电磁学

比奥-萨伐尔定律
$$
\vec B = \oint\frac{\mu_0}{4\pi}\frac{I\mathrm d\vec l}{r^2}\times \hat{\vec r}
$$
常用结论：

- 通电直导线 $B = \dfrac{\mu_0I}{2\pi r}$

安培定律
$$
\oint B \mathrm dl = \mu_0 I
$$
电感

## Math & Misc

### Vectors

**矢量**是有方向有大小的量。

- 常见矢量

  - 位矢 $\vec r$：定义为坐标原点 $O$ 到某点 $P$ 的位移，$\vec r := \overrightarrow{OP}$。

- 矢量求和

- 矢量积

  - 矢量内积
  - 矢量外积
    - 右手法则
    - 左手法则：洛伦兹力

- 矢量的分解

  - 正交分解

    - 物块放置于倾斜角为 $\theta$ 的斜面

      - 重力平行于斜面的分量 $mg\sin\theta$

        - > The object *"slides" ($\sin$)* down the slope.

      - 重力垂直于斜面的分量 $mg\cos\theta$

###  Calculus

列举实用的结论

#### *Differentials*

链式法则
$$
(f\circ g)^\prime = (f^\prime \circ g)\cdot g^\prime
$$

#### *Integrals*

牛顿-莱布尼茨公式
$$
\int_a^b f(x)\mathrm dx = F(b) - F(a)\quad\text{(where $F^\prime(x) = f(x)$)}
$$
函数在闭区间上的均值

> 例：求力 $F(t)$ 在时间 $t_1$ 至 $t_2$ 的均值。

$$
F_\text{avg} = \frac{\int_{t_1}^{t_2}F\mathrm dt} {t_2 - t_1}
$$

常用积分二级结论
$$
\int \frac{A}{kx+b}\mathrm dx = \frac{A}{k}\ln \bigl|kx+b\bigr| + C
$$

#### *First-order Ordinary Differential Equations*

分离变量求解。

一个例子见[阻力正比于速度的自由落体](####阻力正比于速度的自由落体)。

在物理中，这种微分方程在求解时经常带有积分上下限 (定积分)，这种方法也可以使用。
