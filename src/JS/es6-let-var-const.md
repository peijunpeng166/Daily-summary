var let const 用法与区别
在es6中添加了会块级作用域，也就衍生了let和const两种新的变量声明的方式

ES6中新增添的let和const都是支持块级作用域的

https://juejin.cn/post/6844903776512393224#heading-73

1：变量提升  var 存在变量提升 let 和const不会

console.log(a) // 正常运行，打印出 undefined
var a = 1
------------------------
console.log(b) // 报错，Uncaught ReferenceError: b is not defined
let b = 1
------------------------
console.log(c) // 报错，Uncaught ReferenceError: b is not defined
const c = 1

2：暂缓性死区
如果一个代码块中使用了const 或 let 命令，那么它所声明的变量就会被绑定在这个区域，不再受外部的影响
var tmp = 123;
if (true) {
  tmp = 'abc'; // ReferenceError
  let tmp;
}
ES6 中规定，如果代码块内，存在let 或 const，那么这个代码块内声明的变量，从一开始就会形参封闭区域。凡是在声明之前就使用这些变量，就会报错，在语法上，称为"暂时性死区"

3重复声明  var 可以重复声明 let const不可以

4 在ES5 中只用全局作用域和函数作用域，没有块级作用域，这会带来很多不合理的场景

一、内层变量可能会覆盖外层变量
var tmp = new Date();//处于全局作用域

function fn() {
  console.log(tmp);//处于函数作用域
  if (false) {
    var tmp = 'hello world';
  }
}

fn(); // undefined

二、用来计数的循环变量，泄露覆盖全局变量

var i = 10;
for(var i = 0;i < 5;i++){
  console.log(i);
}
console.log(i);// 输出 5