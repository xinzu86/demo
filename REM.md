# webApp页面构建解决方案
## 1、页面构建规范

## 2、retina屏适配

## 3、多尺寸屏幕适配
### rem 是相对于 html 元素的 font-size 的一个单位。如果 html 上定义了 font-size: 20px;则无论在任何地方都是 1rem = 20px 这个大小不会受到父元素的影响。换言之,若整站需要适应页面大小的任何元素都使用 rem 为单位来定义,当设备屏幕变大或者缩小时,我们只需要改变html元素的font-size,那么整站使用了rem单位的元素都会相应的等比放大或者缩小,并且布局不会乱。
* 10px = 1rem 在根元素（font-size = 10px的时候）；
* 20px = 1rem 在根元素（font-size = 20px的时候）；
* 40px = 1rem 在根元素（font-size = 40px的时候）；
```javascript
<script>
(function (doc, win) {
    var docEl = doc.documentElement,
    resizeEvt = 'orientationchange' in window ? 'orientationchange' : 'resize',
    recalc = function () {
        var clientWidth = docEl.clientWidth;
        if (!clientWidth) return;
        docEl.style.fontSize = 20 * (clientWidth / 320) + 'px';
    }
    if (!doc.addEventListener) return;
    win.addEventListener(resizeEvt, recalc, false);
    doc.addEventListener('DOMContentLoaded', recalc, false);
})(document, window);
</script>
```
* 通过CSS @media对HTML字号进行修改也可进行多屏适配，只是没有JS那么灵活。
```css
html {
    font-size : 20px;
}
@media only screen and (min-width: 401px){
    html {
        font-size: 25px !important;
    }
}
@media only screen and (min-width: 428px){
    html {
        font-size: 26.75px !important;
    }
}
@media only screen and (min-width: 481px){
    html {
        font-size: 30px !important; 
    }
}
@media only screen and (min-width: 569px){
    html {
        font-size: 35px !important; 
    }
}
@media only screen and (min-width: 641px){
    html {
        font-size: 40px !important; 
    }
}
```
## 其它