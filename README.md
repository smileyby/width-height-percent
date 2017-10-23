# 什么决定元素自身百分比宽高的大小？

通常情况下，元素的百分比宽高是受到其父元素宽高的影响的。但并不都是这样的。

下面我们用几个实例来验证一下：

```html

<body>
	<div class="outer">
		<div class="inner">
			<p></p>
		</div>
	</div>
</body>

```

## 实例1（无定位样式）：

```css

* {
    margin: 0;
    padding: 0;
}

.outer {
    width: 500px;
    height: 300px;
    background-color: #a95454;
}

.inner {
    width: 300px;
    height: 200px;
    background-color: #444465;
}

p {
    /*position: relative;*/
    width: 50%;
    height: 50%;
    background-color: #afafaf;
}

``` 

效果图：

![http://oqpmmru7y.bkt.clouddn.com/QQ%E6%88%AA%E5%9B%BE20171023193229.png](http://oqpmmru7y.bkt.clouddn.com/QQ%E6%88%AA%E5%9B%BE20171023193229.png)

结果：

p元素设置的宽高，在未设置定位或者定位`position:relative;`时宽高获取的是父元素宽高的百分比。

## 实例2（有定位样式，且不是relative）：

```css

* {
    margin: 0;
    padding: 0;
}

.outer {
    width: 500px;
    height: 300px;
    background-color: #a95454;
}

.inner {
    width: 300px;
    height: 250px;
    background-color: #444465;
}

p {
    position: absolute;
    width: 50%;
    height: 50%;
    background-color: #afafaf;
}

```

效果图：

![http://oqpmmru7y.bkt.clouddn.com/QQ%E6%88%AA%E5%9B%BE20171023194306.png](http://oqpmmru7y.bkt.clouddn.com/QQ%E6%88%AA%E5%9B%BE20171023194306.png)

```css

* {
    margin: 0;
    padding: 0;
}

.outer {
	position: relative;
    width: 500px;
    height: 300px;
    background-color: #a95454;
}

.inner {
    width: 300px;
    height: 250px;
    background-color: #444465;
}

p {
    position: absolute;
    width: 50%;
    height: 50%;
    background-color: #afafaf;
}

```

效果图：

![http://oqpmmru7y.bkt.clouddn.com/QQ%E6%88%AA%E5%9B%BE20171023194640.png](http://oqpmmru7y.bkt.clouddn.com/QQ%E6%88%AA%E5%9B%BE20171023194640.png)

```css

* {
    margin: 0;
    padding: 0;
}

.outer {
    width: 500px;
    height: 300px;
    background-color: #a95454;
}

.inner {
    position: relative;
    width: 300px;
    height: 200px;
    background-color: #444465;
}

p {
    position: absolute;
    width: 50%;
    height: 50%;
    background-color: #afafaf;
}

```

效果图：

![http://oqpmmru7y.bkt.clouddn.com/QQ%E6%88%AA%E5%9B%BE20171023194749.png](http://oqpmmru7y.bkt.clouddn.com/QQ%E6%88%AA%E5%9B%BE20171023194749.png)

```css

* {
    margin: 0;
    padding: 0;
}

.outer {
    width: 500px;
    height: 300px;
    background-color: #a95454;
}

.inner {
    position: relative;
    width: 300px;
    height: 200px;
    background-color: #444465;
}

p {
    position: fixed;
    width: 50%;
    height: 50%;
    background-color: #afafaf;
}

```

效果图：

![http://oqpmmru7y.bkt.clouddn.com/QQ%E6%88%AA%E5%9B%BE20171023195401.png](http://oqpmmru7y.bkt.clouddn.com/QQ%E6%88%AA%E5%9B%BE20171023195401.png)

结论：

1. p标签定位属性为（fixed）时，不论父元素是否具有定位属性，p标签的宽高百分比由body的宽高决定
2. p标签定位属性为（absolute）时，p标签的宽高百分比有距离其最近的具有定位属性的父辈元素的宽高决定，若其所有父元素都不具备定位属性，则p标签的宽高百分比有body的宽高决定

* 以上为个人测试观点，如有不对之处请批评指正。

