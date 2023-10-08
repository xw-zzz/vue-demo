# 说明
学习Vue的一些代码示例及相关笔记，学习视频教程地址：[尚硅谷](https://www.bilibili.com/video/BV1Zy4y1K7SH/?p=18&spm_id_from=pageDriver&vd_source=a4f81a5a4125fada8aa1a3f14c2fddbc)

# 笔记

## vue事件

### 基本使用

  1.使用V-on:xxx或@xxx绑定事件，其中xxx是事件名：

  2.事件的回调需要配置在methods.对象中，最终会在vm上：

  3.methods中配置的函数，不要用箭头函数！否则this就不是vm了：

  4.methods中配置的函数，都是被Vue所管理的函数，this的指向是vm或组件实例对象：

  5.@c1ick="demo”和@click=:"demo($event)"效果一，但后者可以传参

### 修饰

- prevent:阻止默认事件（常用）：
- stop:阻止事件冒泡（常用）；
- once:事件只触发一次（常用）：
- capture:使用事件的捕获模式：
- self:只有event.target是当前操作的元素时才触发事件：
- passive:事件的默认行为立即执行，无需等待事件回调执行完毕

代码示例：

```html

        <div class="demo1" @click="showInfo">
            <button @clock.stop="showInfo">点我提示信息</button>
            
            <a href="http://www.atguigu.gom"@click.prevent.stop="showInfo">点我提示信息</a>
        </div>
```

### 键盘事件

  回车=>enter

  删除=>delete(捕获“删除”和退格”键)

  退出=esc

  空格=>space

  换行=>tab

  上=>up

  下=>down

  左=>1eft

  右=>right

  2.Vue未提供别名的按键，可以使用按键原始的key值去绑定，但注意要转为kebab-case(短横线命名)

  3.系统修饰键（用法特殊）：ctrl、at、shift、meta

  (1).配合kyup使用：按下修饰键的同时，再按下其他键，随后释放其他键，事件才被蚀发。

  (2).配合keydown使用：正常触发事件。

  4.也可以使用keyCode去指定具体的按键（不推荐）

  5.Vue.config.keyCodes.自定义键名=键码，可以去定制按键别名

```
    <div id="root">
       <input type="text" placeholder="按下回车提示输入" @keyup.enter="showInfo"></input>
    </div>
```

