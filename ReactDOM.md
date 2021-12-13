### render

render的源码代码如下：

```typescript
  render(
    element: React$Element<any>,
    container: DOMContainer,   //判断是否是DOM节点
    callback: ?Function,
  ) {
    return legacyRenderSubtreeIntoContainer(
      null,
      element,
      container,
      false,
      callback,
    );
  },
```

实则在一般class组件调用时的写法是：

```react
import React from 'react'
export  default class Home extends React.Component{   //继承react包中的Component类
    //此处继承了render方法之后，并没有传值，而是重写该方法了，直接返回了
    render(){    //render方法是ReactDOM中定义的，暂不知为什么在React.Component中，同一个原型链？
        return (
            <h1>ajiao</h1>
        )
    }
}
```

关于继承后方法重写，参照以下例子：

```js
class  AA {    //定义了一个类AA，有方法aa和bb
    aa(a,b,c){
        return this.bb(a,b,1)
    }
    bb(a,b){
        console.log(a+b)
    }
}


class BB extends AA{    定义类BB继承AA类，即继承了AA的方法
    aa(){      //此处重写了aa方法，直接返回2+2
        return 2+2
    }
}

let cc=new BB()     //let一个BB实例


console.log(cc)    //此处可以看到cc的整个原型链
console.log(cc.aa(1,2))   //返回的是4，即调用的是重写后的aa方法
```

![image-20211213143724939](C:\Users\ajiao\AppData\Roaming\Typora\typora-user-images\image-20211213143724939.png)