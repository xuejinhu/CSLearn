[Markdown 引用语法 | Markdown 官方教程](https://markdown.com.cn/basic-syntax/blockquotes.html)

？？？SICP=》信息的表示、处理的逻辑、设计抽象

<span style="color: red;">TODO:[命令行的使用 cls1-3](https://github.com/anthonyjatoba/missing-semester/tree/master) + [cls 6](https://www.bilibili.com/video/BV14E411J7n2/)</span>



## 1.2 编程要素

### 1.2.1 变量与环境

**某个环境下**：变量=值（<u>名称 绑定</u>到了<u>值</u>上）

```python
>>> x = 1
>>> y = 2
>>> x,y = y,x
>>> x
2
>>> y
1
```

> 所有 `=` 右边的表达式都会先求值，然后再与左边的名称绑定

### 1.2.2 求解嵌套表达式

Operator(Operand,Operand)

```python
>>> sub(pow(2, add(1, 10)), pow(2, 5))
2016
```

> 利用表达式树

```python
def if_function(condition, true_result, false_result):
    """Return true_result if condition is a true value, and
    false_result otherwise.

    >>> if_function(True, 2, 3)
    2
    >>> if_function(False, 2, 3)
    3
    >>> if_function(3==2, 3+2, 3-2)
    1
    >>> if_function(3>2, 3+2, 3-2)
    5
    """
    if condition:
        return true_result
    else:
        return false_result


def with_if_statement():
    """
    >>> result = with_if_statement()
    2
    >>> print(result)
    None
    """
    if c():
        return t()
    else:
        return f()

def with_if_function():
    """
    >>> result = with_if_function()
    1
    2
    >>> print(result)
    None
    """
    return if_function(c(), t(), f())

def c():
    "*** YOUR CODE HERE ***"
    return False

def t():
    "*** YOUR CODE HERE ***"
    print(1)

def f():
    "*** YOUR CODE HERE ***"
    print(2)
```



## 1.3 定义函数UDF

### 1.3.1 定义

```
def <name>(<formal parameters>):
	return <return expression>
```

> 函数名和参数名称是小写的，单词之间用下划线分隔

### 1.3.2 核心属性

- **域** 是任意单个实数。
- **范围** 是任意非负实数。
- **意图** 是计算输入的平方作为输出。

### 1.3.3 运作逻辑

1. 在新的局部帧中，将实参绑定到函数的形参上。
2. 在以此帧开始的环境中执行函数体。

> **名称求解（Name Evaluation）**:先找局部帧,再找全局帧

### 1.3.4 描述文档

```python
>>> def test(n):
...     """just test"""
...     print(1)
...
>>> help(test)
Help on function test in module __main__:

test(n)
    just test
```

### 1.3.5 测试

```
 python -i lab00.py
```

> -i  interactive 进入交互模式

- 编写

```
# 第一种
def fib_test():
	assert fib(2) == 1, '第二个斐波那契数应该是 1'
	assert fib(3) == 1, '第三个斐波那契数应该是 1'
	assert fib(50) == 7778742049, '在第五十个斐波那契数发生 Error'

# 第二种
def sum_naturals(n):
    """返回前 n 个自然数的和。

    >>> sum_naturals(10)
    55
    >>> sum_naturals(100)
    5050
    """
    total, k = 0, 1
    while k <= n:
    	total, k = total + k, k + 1
    return total
```

- 启动

```
# 特定函数
from doctest import run_docstring_examples
run_docstring_examples(sum_naturals, globals(), True)

# 启动所有
python3 -m doctest <python_source_file>
```



