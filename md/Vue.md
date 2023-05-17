#  VUE

## 一. 简介

```javascript
         new Vue({
            el:'#root',
            data:{
            name:'双向绑定',
        }
         })
```



### 1.1 模板语法

插值语法：用于修改标签中的文本: `{{}}`
指令语法：用于操作标签的属性: `v-bind`

### 1.2 绑定方式

单向绑定：v-bind :属性 ====> : 属性
双向绑定：v-model:value  ====> v-model  用于操作表单类属性

el ===> vm.$mount('css选择器')
data ===> data(){ retun数据对象 }：函数返回值为对象处理data

### 1.3 MVVM模型

![2023-05-14_205606](C:\Users\zb15746197413\Desktop\vue\md\2023-05-14_205606.png)

data====> Vue实例处理 ==\==>DOM渲染

### 1.4 数据的代理

Objct.defineproperty() //使多个对象属性管理一个变量（数据代理）

![2023-05-15_160600](C:\Users\zb15746197413\Desktop\vue\md\2023-05-15_160600.png)

#### 配置对象作用

+ 将data对象拷贝一份作为vue实例对象的 _data对象值:

  ...to be continued 

+ 通过数据代理 将 ==_data 的属性方法==添加到==vue实例对象==中( 简化属性获取)

+ 这两个对象 都可以访问 修改属性 （getter，setter）

### 1.5事件

#### 事件处理

+ v-on：e ===> @e
+ 传参 ： @click= 'change($event, )':传入多个参数包含事件对象

#### 事件修饰符号

``@click.prevent='change'`:阻止默认事件

+ prevent ：阻止默认事件（a点击后的跳转）

+ stop ：阻止冒泡，（点击后防止父元素也触发相同事件）

+ once ：该事件只能触发一次

+ capture：默认情况下浏览器事件使冒泡阶段执行；

  ​                  此属性可修改为捕获阶段

+ self：只有e.target是当前元素时候触发（一定情况下阻止冒泡了）

+ pssive：事件默认行为立即执行，无需等事件回调执行完

  滚动事件事件：  scroll 直接先处理默认事件

  ​                               wheel（默认先执行回调，后滚动）移动端优化

#### 键盘事件

`@keyup.enter='change()'`

+ 回车 => enter
+ 删除 => delete
+ 退格 => esc
+ 空格 => space
+ 换行 =>tab
+ up down left right

Vue为提供别名的案件，可以用按键的key值去绑定 但是要转换为 kebad-case（短线命名）

自定义键名：Vue.config.keyCodes.自定义名 = 键码

注意系统按键 keydown 与keyup不同