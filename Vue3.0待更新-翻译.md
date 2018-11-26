# Vue3.0 Updates
> - 资料来源大神 Evan You
> - 本文只是翻译和自己的一点期望

## Vue3.0将带来哪些变化？
> - 更快
> - 更小
> - 更易于维护
> - 更易于切合原生API
> - 状态管理更容易

### 更快
> - 重写Virtual DOM 底层实现机制
> - 挂载和patch(根据dom-diff计算差异结果)更加快捷

### 更多编译时优化以减少运行时的开销
> - 背景：运行时Template中有些不会变化的地方，vitrual dom也会重新生成节点，并dom-diff，这个开销还蛮大的，并不必要
> - 解决方案:在编译时分析，对其优化
> - 2.0时，不管是自定义组件还是原生html标签，都是要传到 h 函数中（h是创建虚拟node的函数,比对），这些是在运行时进行的，因此开销很大
> - 3.0: 模版编译时，判断自定义与原生标签,直接生成组件和原生的东西，并且留下是否含有子元素的标记，运行时可以减少开销 
> - 组件快速路径
> - 单一调用方式
> - 子组件类型检测

> - 跳过不必要的条件分支
> - JS引擎优化

![](readImg1/a.png)

> - 静态内容提取
> - 忽略计算整个树的差异
> - 即使出现多个static tree，也能提升

![](readImg1/b.png)

> - 静态属性提取 
> - 跳过DOM节点本身的patch,而保留子节点的patch

![](readImg1/c.png)

> - 内联方法提升
> - 避免由于内联函数标识不同，而引起的不必要的重新渲染

![](readImg1/d.png)

### 基于proxy代理模式 替代 原来的观察者模式，性能更优
> - 全部使用ES6来实现
> - Property addition/ deletion
> - Array index / length mutation
> - Map,Set, WeakMapm,WeakSet
> - Classes
#### 使用ES6 proxy 监听对象实例的属性
#### 利用Proxy减少组件实例初始化开销
#### 优化内存，事半功倍，(一半的内存,两倍速率)
![](readImg1/e.png)

### 代码更小
> - 更友好的Tree-shaking (按需引用)
> > - 内置组件(keep-alive,transition...µ)
> > - 指令的运行时(v-model,v-for...)
> > - 公共函数(异步组件、mixins...)
> - 核心功能: 压缩后10kb 

### 更易于维护
> - 使用 TypeScript
> - 解耦依赖包
![](readImg1/f.png)
> - 重写编译器（插件化）

### 更易于切合原生API
![](readImg1/g.png)

### 状态管理更容易
> - 响应式监听 API（目的是为了跨组件状态共享）
![](readImg1/h.png)
> - 轻松排查组件更新的触发原因
![](readImg1/j.png) 



