# 作业二 Python变量和列表

- 班级： 22物联1班

- 学号： 202202200000

- 姓名： 张三

---

## 第1题：求离整数n最近的平方数（Find Nearest square number）

难度：8kyu

你的任务是找到一个正整数n的最近的平方数
例如，如果n=111，那么nearest_sq(n)（nearestSq(n)）等于121，因为111比100（10的平方）更接近121（11的平方）。
如果n已经是完全平方（例如n=144，n=81，等等），你需要直接返回n。
代码验证地址
<https://www.codewars.com/kata/5a805d8cafa10f8b930005ba>

```python
# 请在这里填写你的代码
import math

def nearest_sq(n):
    # 计算 n 的平方根并向下取整
    root = int(math.sqrt(n))
    
    # 计算下一个平方数和当前平方数
    lower_sq = root ** 2
    upper_sq = (root + 1) ** 2
    
    # 如果 n 已经是完全平方数，则直接返回 n
    if n == lower_sq:
        return n
    
    # 返回最近的平方数
    if (n - lower_sq) < (upper_sq - n):
        return lower_sq
    else:
        return upper_sq

# 测试函数
print(nearest_sq(111))  # 输出 121
print(nearest_sq(144))  # 输出 144


```

## 第2题：偶数或者奇数（Even or Odd）

难度：8kyu

创建一个函数接收一个整数作为参数，当整数为偶数时返回”Even”当整数为奇数时返回”Odd”。
代码验证地址：
<https://www.codewars.com/kata/53da3dbb4a5168369a0000fe>

```python
# 请在这里填写你的代码
def even_or_odd(number):
    return "Even" if number % 2 == 0 else "Odd"

print(even_or_odd(2))  # 输出 "Even"
print(even_or_odd(3))  # 输出 "Odd"

```

## 第三题：括号匹配（Valid Braces）

难度：6kyu

写一个函数，接收一串括号，并确定括号的顺序是否有效。如果字符串是有效的，它应该返回True，如果是无效的，它应该返回False。
例如：

```python
"(){}[]" => True 
"([{}])" => True
 "(}" => False
 "[(])" => False 
"[({})](]" => False
```

**提示：
python中没有内置堆栈数据结构，可以直接使用`list`来作为堆栈，其中`append`方法用于入栈，`pop`方法可以出栈。**

代码验证地址
<https://www.codewars.com/kata/5277c8a221e209d3f6000b56>

```python
# 请在这里填写你的代码
def valid_braces(string):
    # 定义一个栈来存储开放的括号
    stack = []
    
    mapping = {')': '(', '}': '{', ']': '['}
    
    for char in string:
        # 如果是开放括号，入栈
        if char in mapping.values():
            stack.append(char)
        # 如果是闭合括号，检查栈顶元素
        elif char in mapping.keys():
            # 检查栈是否为空且栈顶元素是否匹配
            if not stack or stack.pop() != mapping[char]:
                return False
    
    # 返回栈是否为空（所有括号是否都已匹配）
    return len(stack) == 0

print(valid_braces("(){}[]"))    # 输出 True
print(valid_braces("([{}])"))     # 输出 True
print(valid_braces("(}"))         # 输出 False
print(valid_braces("[(])"))       # 输出 False
print(valid_braces("[({})](]"))   # 输出 False

```
