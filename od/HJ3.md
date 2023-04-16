## HJ3 明明的随机数
题目链接：[明明的随机数](https://www.nowcoder.com/practice/3245215fffb84b7b81285493eae92ff0?tpId=37&tqId=21226&rp=1&ru=/exam/oj/ta&qru=/exam/oj/ta&sourceUrl=%2Fexam%2Foj%2Fta%3FtpId%3D37&difficulty=undefined&judgeStatus=undefined&tags=&title=)

描述：

明明生成了NN个1到500之间的随机整数。请你删去其中重复的数字，即相同的数字只保留一个，把其余相同的数去掉，然后再把这些数从小到大排序，按照排好的顺序输出。

数据范围： 1≤n≤1000 ，输入的数字大小满足 1≤val≤500 

输入描述：

第一行先输入随机整数的个数 N 。 接下来的 N 行每行输入一个整数，代表明明生成的随机数。 具体格式可以参考下面的"示例"。

输出描述：

输出多行，表示输入数据处理后的结果

示例1
```html
输入：3
	  2
	  2
	  1

输出：1
	  2

说明：输入解释：
		第一个数字是3，也即这个小样例的N=3，说明用计算机生成了3个1到500之间的随机整数，接下来每行一个随机数字，共3行，也即这3个随机数字为：
		2
		2
		1
		所以样例的输出为：
		1
		2       
```

## 解题思路 & 编码实现
借助 JS 的 includes()，判断数组中是否包含指定的值，包含即跳过该数据，从而得到去重的效果。

## 代码

```javascript
const rl = require("readline").createInterface({ input: process.stdin });
var iter = rl[Symbol.asyncIterator]();
const readline = async () => (await iter.next()).value;

void (async function () {
    // Write your code here
    while ((line = await readline())) {
        // 存放随机整数的数组
        let arr = [];
        let num = 0;
        for (let i = 0; i < line; i++) {
            num = await readline();
            // 判断数组中是否包含生成的随机数，不包含即放入数组
            if(!arr.includes(num)) {
                arr.push(num);
            }
        }
        // 排序从小到大，换行输出
        console.log(arr.sort((a, b) => a-b).join("\n"))
    }
})();
```