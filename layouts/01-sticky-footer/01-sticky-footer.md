```css
flex: auto;
```
flex 属性是 `flex-grow`、`flex-shrink`、`flex-basis` 这三个属性的缩写。
> CSS 官方推荐使用缩写。
按照以往的经验，flex 缺省值应该为默认才是。使用以下代码获取默认值：
```js
getComputedStyle(document.body).flexGrow // 0
getComputedStyle(document.body).flexShrink // 1
getComputedStyle(document.body).flexBasis // auto
```
然后看下 `flex` 缩写属性的计算值，就会发现不一样的事情：

`flex:1` 等同于 `flex:1 1 0%`，`flex:1 2` 等同于 `flex:1 2 0%`，即 `flex-basis` 使用的不是默认值auto，而是使用的0%；
`flex:100px` 等同于 `flex:1 1 100px`，即 `flex-grow` 使用的不是默认值0，而是使用的1。
> flex属性站在实用主义的角度对缩写属性的计算值进行了优化。

常见的flex缩写有下面这几个，`flex:0`、`flex:1`、`flex:none`、`flex:auto`，那各个CSS声明应该在什么场景下使用才正确呢？

> flex: initial; flex: 0 1 auto	初始值，常用  
> flex: 0;	flex: 0 1 0%	适用场景少  
> flex: none;	flex: 0 0 auto	推荐  
> flex: 1;	flex: 1 1 0%	推荐  
> flex: auto;	flex: 1 1 auto	适用场景少

结合flex属性值的描述，我们可以得出flex:1和flex:auto的行为表现：
> 元素尺寸可以弹性增大，也可以弹性变小，具有十足的弹性，但是flex:1在尺寸不足时会优先最小化内容尺寸，flex:auto在尺寸不足时会优先最大化内容尺寸。

flex:initial表示默认的flex状态，无需专门设置，适合小控件元素的分布布局，或者某一项内容动态变化的布局；  
flex:0适用场景较少，适合设置在替换元素的父元素上；  
flex:none适用于不换行的内容固定或者较少的小控件元素上，如按钮；  
flex:1适合等分布局；  
flex:auto适合基于内容动态适配的布局；  

> https://www.zhangxinxu.com/wordpress/2020/10/css-flex-0-1-none/