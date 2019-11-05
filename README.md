# jsArray
13个JS 数组精简技巧



# 1.删除数组的重复项

array.from()

​	将一个`类数组对象`或者可遍历对象转换成一个真正的数组。

new Set()

​	用来数组去重

```javascript

var fruits = ["apple","apple","banana","orange"];
// 第一种方式
var uniqueFruits = Array.from(new Set(fruits));
console.log(uniqueFruits);//["apple","banana","orange"]

// 第二种方式
var uniqueFruits = [...new Set(fruits)];   //...是ES6的解构赋值
console.log(uniqueFruits);//["apple","banana","orange"]
```



# 2.替换数组中的特定值

splice(start,value to remove,valueAdd):

​	start:操作开始的索引位置

​	value to remove:要替换的个数（如果num为0，就是插入功能）

​	valueAdd:替换的值

```javascript

var fruits = ["apple","apple","banana","orange"];
fruits.splice(0,2,"pear","peach");
console.log(fruits); //["pear","peach","banana","orange"]

```



# 3.Array.from达到map的效果

map()

​	可以创建一个`新数组`，其结果是`该数组`中的每个元素都调用一个提供的函数后返回的`结果`。操作的对象必须是一个纯数组。

```javascript
var student = [
    {name:"zhangsan",age:12,sex:"nan"},
    {name:"lisi",age:13,sex:"nan"},
    {name:"xiaohong",age:10,sex:"nv"},
    {name:"xiaoming",age:12,sex:"nan"},
    {name:"xiaoli",age:14,sex:"nv"}
];
var studenName = Array.from(student,({name}) => name);
console.log(studenName); //["zhangsan","lisi","xiaohong","xiaoming","xiaoli"]
```



# 4.置空数组

我们要清空一个数组的时候，最快捷的方法就是直接让他的length为0

```javascript
var student = [
    {name:"zhangsan",age:12,sex:"nan"},
    {name:"lisi",age:13,sex:"nan"},
    {name:"xiaohong",age:10,sex:"nv"},
    {name:"xiaoming",age:12,sex:"nan"},
    {name:"xiaoli",age:14,sex:"nv"}
];
student.length = 0;
console.log(student);//[]
```



# 5.将数组转换成对象

将数组转换成对象最简单快速的方法就是使用ES6的扩展运算符（...）
扩展运算符（...）用于取出参数对象的所有可遍历属性，拷贝到当前对象之中

```javascript
var arr = [0, 1, 2, 3, 4, 5];
var arrObj = { ...arr };
console.log(arrObj);  //{0: 0,1: 1,2: 2,3: 3,4: 4,5: 5}      
```



# 6.用数据填充/替换数组

有时候我们创建了一个数组并希望用一些数据来填充他们的时候，可以使用fill()方法。

fill(value, start, end)

​	value:必需。填充的值

​	start:开始填充的位置

​	end:停止填充的位置（默认为array.length）

```javascript

//填充
var arr = new Array(2).fill('1');
console.log(arr);  //["1","1"] 

//替换
var fruits = ["apple","apple","banana","orange"]
var newFruits = fruits.fill('apple',2,3);
console.log(newFruits); //["apple","apple","apple","orange"]

```



# 7.求两个数组的交集

要找到两个数组的交集，首先要确保数组中的值不重复（做去重操作），接着使用filter方法和includes方法

filter()

​	创建一个新数组，新数组中的元素是通过检查指定数组中符合条件的所有元素。不会对空数组进行检测，也不会改变原始的数组

includes()

​	用来判断一个数组中是否包含一个指定的值	，返回的是布尔值

```

var arr1 = [0, 1, 1, 2, 3, 4];
var arr2 = [1, 3, 5, 7];
var duplicatedValus = [...new Set(arr1)].filter(item => arr2.includes(item));
console.log(duplicatedValus);//[1, 3]

```



# 8.从数组中删除虚值

虚值：在`Boolean上`下文中已经认定可转化为”假“的值。

在JS中，虚值有 false、0、''、null、NaN 、undefined

```javascript

var arr =['','ceshi',false,0,NaN,null,undefined];
console.log(arr.filter(Boolean)); //["ceshi"]

```



# 9.从数组中获取随机值

可以根据数组长度获得一个随机索引，来获取随机值

```javascript

var arr = ["随机数1","随机数2","随机数3","随机数4","随机数5","随机数6","随机数7"];
console.log(arr[Math.floor(Math.random() * arr.length )]);
        
```



# 10.反转数组

reverse()

​	用于颠倒数组中元素的顺序

```javascript

var arr = ["随机数1","随机数2","随机数3","随机数4","随机数5","随机数6","随机数7"];
console.log(arr.reverse());

```



# 11.lastIndexOf()方法

#### indexof和lastIndexOf的比较

* 都是索引文件
* indexOf是查看某个元素**首次**出现的位置，lastIndexOf是查看某个元素**最后一次**出现的位置。



# 12.对数组中的所有值求和

reduce()

```javascript

var arr = [1,1,1,1];
console.log(arr.reduce( (x , y) => x +y ));

```



# 13.其他



* arr.push()

  * 从后面添加元素，返回值为添加后的数组长度

* arr.pop()

  * 从后面删除元素，只能是一个，返回值是删除的元素

* arr.shift()

  * 从前面删除元素，只能删除一个，返回值是删除的元素

* arr.unshift()

  * 从前面添加元素，返回值是添加后的数组长度

* arr.concat()

  * 连接两个数组，返回值是连接后的新数组

* arr.split()

  * 将字符串转化为数组

* arr.sort()

  * 将数组进行排序，返回值是排好的数组，默认是按照最左边的数字进行排序，不是按照数字的大小进行排序的

  ```javascript
  let arr = [2,10,6,1,4,22,3]
  console.log(arr.sort())   // [1, 10, 2, 22, 3, 4, 6]
  let arr1 = arr.sort((a, b) =>a - b)  
  console.log(arr1)   // [1, 2, 3, 4, 6, 10, 22]
  let arr2 = arr.sort((a, b) =>b-a)  
  console.log(arr2)  // [22, 10, 6, 4, 3, 2, 1]
  ```

* arr.slice(start,end)

  * 切去开始start到结束end的数组，不包含end索引值的值，返回值是切出来的数组

* arr.forEach()

  * 遍历数组，无return





