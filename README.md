//栈是一种后入先出LIFO,last-in-first-out的数据结构
//所以任何不在栈顶的元素都无法访问，对栈的操作主要是将元素压入push和弹出pop；peek用于查看栈顶的元素；
//定义stack类的构造函数，和相关操作；
function Stack(){
    this.dataStore=[];
    this.top=0;
    this.push=push;
    this.pop=pop;
    this.peek=peek;
    this.clear=clear;
    this.length=length;
}
function push(element){
    return this.dataStore[this.top++]=element;
}
function pop(element){
    return this.dataStore[--this.top];
}
function peek(element){
    return this.dataStore[this.top-1]
}
function length(){
    return this.top
}
function clear(){
    this.top=0;
}
var s=new Stack();
s.push("David");
s.push("raymond");
s.push("bryan");
console.log(s.length());
console.log(s.peek());
var popped= s.pop();
console.log("删除的元素是："+popped,"s的长度是："+s.length());
s.push("Cythia");
console.log("顶部的元素是："+s.peek(), "s的长度是："+s.length());



//使用栈来实现数制间的相互转换
//实现的算法如下：
//1，最高位为n%b，将此位压入栈；
//2，使用n/bd代替n；
//3，重复步骤1和2，直到n等于0，且没有余数；
//4，持续将栈内元素弹出，直到栈为空，依次将元素排列，直到得到转换后数字的字符串形式。
function mulBase(num,base){
    var s=new Stack();
    do{
        s.push(num%base);
        num=Math.floor(num/=base);
    }while(num>0);
    var converted="";
    while(s.length()>0){
        converted+= s.pop();
    }
    return converted;
}

//我们来测试一下：
var num=32;
var base=2;
var newNUm=mulBase(num,base);
console.log(num + "转换成" + base + "进制是：" + newNUm);
var num=125;
var base=8;
var newNUm=mulBase(num,base);
console.log(num + "转换成" + base + "进制是：" + newNUm);


//使用栈来判断是否是回文
//回文：从前往后写和从后网前些是一样的
//实现：
// 1.将字符串的每个字符按照从左往右顺序压入栈；
// 2.持续弹出栈内的每个字母，得到新的字符串；
//3.如果两个字符串相等，结果是回文；否则返回false
function isPalindrome(word){
    var s=new Stack();
    for(var i=0;i<word.length;++i){
        s.push(word[i])
    };
    var rword="";
    while(s.length()>0){
        rword+= s.pop();
    }
    if(word==rword){
        return true
    }else{
        return false
    }
}
//现在我们开始测试代码
var word="hello";
var result=word+"是回文"+isPalindrome(word);
console.log(result);
var word="racecar";
var result=word+"是回文:"+isPalindrome(word);
console.log(result);


//递归模拟演示：阶乘
//下面是一个递归函数
function factorial(n){
    if(n===0){
        return 1
    }else{
        return n*factorial(n-1)
    }
}
//使用栈来模拟计算
function fact(n){
    var s=new Stack();
    while(n>1){
        s.push(n--)
    }
    var product=1;
    while(s.length()>0){
        product*= s.pop();
    }
    return product
}
console.log(factorial(5));
console.log(fact(5));
