##observe.js

用于观察任意对象的任意变化的类库，以轻巧、实用、强大而闻名。

ps:源代码未压缩版仅仅只有几十行代码:)

##3分钟精通observe.js

### 对象字面量
```javascript
var obj = { a: 1 };
observe(obj, function (name, value , old) {
    console.log(name + "__" + value + "__" + old);
});
obj.a = 2; //a__2__1 
```

### 数组
```javascript
var arr = [1, 2, 3];
observe(arr, function (name, value, old) {
    console.log(name + "__" + value+"__"+old);
});
arr.push(4);//array__push__4 
arr[3] = 5;//3__5__4
```

### 复杂对象
```javascript
var complexObj = { a: 1, b: 2, c: [{ d: [4] }] };
observe(complexObj, function (name, value ,old) {
    console.log(name + "__" + value + "__" + old);    
});
complexObj.c[0].d = 100;//d__100__4 
```
### 普通对象
```javascript
var User = function (name, age) {
    this.name = name;
    this.age = age;
    //只监听name
    observe(this,["name"] function (name, value, oldValue) {
        console.log(name + "__" + value + "__" + oldValue);
    });
}
var user = new User("lisi", 25);
user.name = "wangwu";//name__wangwu__lisi 
user.age= 20; //什么都输出，因为没有监听age
```


This content is released under the (http://opensource.org/licenses/MIT) MIT License.

