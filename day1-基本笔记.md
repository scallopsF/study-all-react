# react

## 1、创建和嵌套组件

    1 使用一个函数的return， 返回内容为html内容，可以嵌套在另外一个函数中。
    2 嵌套时 组件 第一个字母大写 用于区分普通元素

## 2、使用 jsx 编写标签

    1 返回必须是一个整体 可以用<></> 或者 div 盒子 报起来

## 3、添加样式

    可以使用className来指定一个css的class，然后可以进行样式操作了

## 4、显示数据

     用单个{}来显示数据

## 5、条件渲染

`    let content;
    if (isLoggedIn) {
    content = <AdminPanel />;
    } else {
    content = <LoginForm />;
    }
    return (
    <div>
        {content}
    </div>
    );`

## 6、渲染列表

    在你的组件中，使用 map() 函数将一个产品数组，转换为 <li> 标签的元素列表
    const listItems = products.map(product =>
    `  <li key={product.id}>
        {product.title}
    </li>
    );

    return (
    <ul>{listItems}</ul>
    );`

## 7、响应事件

    通过在组件中声明 事件处理 函数来响应事件：
    ` function MyButton() {
        function handleClick() {
            alert('You clicked me!');
        }

        return (
            <button onClick={handleClick}>
            Click me
            </button>
    );
    } `
    注意，onClick={handleClick} 的结尾没有小括号！不要 调用 事件处理函数：你只需 传递给事件 即可。当用户点击按钮时，React 会调用你的事件处理函数。

## 8、更新界面

通常，你会希望你的组件 “记住” 一些信息并展示出来。例如，也许你想计算一个按钮被点击的次数。要做到这一点，你需要在你的组件中添加 state。

首先，从 React 引入 useState：

import { useState } from 'react';
现在你可以在你的组件中声明一个 state 变量：

function MyButton() {
const [count, setCount] = useState(0);
// ...
你将从 useState 中获得两样东西：当前的 state（count），以及用于更新它的函数（setCount）。你可以给它们起任何名字，但按照惯例，需要像这样 [something, setSomething] 为它们命名。

第一次显示按钮时，count 的值为 0，因为你把 0 传给了 useState()。当你想改变 state 时，调用 setCount() 并将新的值传递给它。点击该按钮计数器将递增：

function MyButton() {
const [count, setCount] = useState(0);

function handleClick() {
setCount(count + 1);
}

return (
<button onClick={handleClick}>
Clicked {count} times
</button>
);
}
React 将再次调用你的组件函数。这次，count 会变成 1。接着，变成 2。以此类推。

## 9、使用 Hook

    以 use 开头的函数被称为 Hook。useState 是 React 提供的一个内置 Hook。你可以在 React API 参考 中找到其他内置的 Hook。你也可以通过组合现有的 Hook 来编写属于你自己的 Hook。

    Hook 比普通函数更为严格。你只能在你的组件（或其他 Hook）的 顶层 调用 Hook。如果你想在一个条件或循环中使用 useState，请提取一个新的组件并在组件内部使用它。

# 组件间共享数据

``` 组件共享数据
import { useState } from 'react';

export default function MyApp() {
const [count, setCount] = useState(0);

function handleClick() {
setCount(count + 1);
}

return (
<div>
<h1>Counters that update together</h1>
<MyButton count={count} onClick={handleClick} />
<MyButton count={count} onClick={handleClick} />
</div>
);
}

function MyButton({ count, onClick }) {
return (
<button onClick={onClick}>
Clicked {count} times
</button>
);
}
```
