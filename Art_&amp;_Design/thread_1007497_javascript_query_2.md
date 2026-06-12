---
title: "javascript query 2"
date: 2008-12-10
forum: Art &amp; Design
---

### Post by maclenin on 2008-12-10
With reference to the following script...

```
var a=("123");
document.write(a + " is the value of a when first assigned" + "</br>");

var b=(a++);
document.write(b + " is the value of b when first assigned" + "</br>");
document.write(a + " is the value of a AFTER b first assigned" + "</br>");
```

...and its output...

```
123 is the value of a when first assigned
123 is the value of b when first assigned
124 is the vaule of a AFTER b is first assigned
```

...can anyone tell me what the statement...

```
var b=(a++);
```

...is actually doing?

I've used **var b=(a++)** to "convert" the numeric string **a** to an integer **b** so that I can perform various operations on string **a** using its integer or **b** form: e.g. (**b**+1), (**b**-1) etc.

However, it also seems the assignation of **a** to **b** via **var b=(a++)** converts **a** into an "unassigned" integer, or "**über a**" with the value (**a**+1)....

The thing I can't figure out is why the "integer value" of **a** doesn't remain exclusively associated with the variable - in this case **b** - to which it was very specifically assigned? Why does a "new" value of **a** spill or leak out of the assignation of **a** to **b**? 

Essentially, how can **a** become an integer if I haven't made it one? How does **a** become "changed" by an operation I've specifically and only assigned to **b**?

Thanks for any clarification!

---

### Post by banago on 2008-12-11
a++ stands for a+1 - this is the same in PHP too.

---

### Post by altonbr on 2008-12-11
Think of it as interesting syntax.

JavaScript is a [loosely]("http://en.wikipedia.org/wiki/Weak_typing") and dynamically typed programming language.

If it said
```
var b= (a+1);
```
the outcome would have been the same.

But if it said
```
var b=(a+"1");
```
then the outcome would have been "1231".

This is a wanted benefit for JavaScript as it is a scripting language, instead of a programming language, where data types do not want to be assumed.

Also,
```
a++
```

is commonly used to indicate a = a + 1 in for loops:
[PHP]for ($a = 0; $a < 10; $a++)
{
    echo '$a = '.$a;
}[/PHP]
and is merely used as a short form.

---

### Post by maclenin on 2008-12-12
**banago:**

and

**altonbr:**

Thanks for the clarification(s)!

I think I was clear, for the most part (save for the PHP reference), on the "meaning" of a++, generally (**banago**), and the "syntax" of javascript, more specifically (**altonbr**), re: (a+1) vs. (a+"1") and so forth....

However, what still puzzles me is...

...**if**...

```
var **a**=("**123**");
```

...**and**...

```
var **b**=(**a++**);
```

...**how** can the output of...

```
document.write(**a**);
```

...be **124**?

Thanks for any additional thoughts....

---

### Post by altonbr on 2008-12-12
> **maclenin said:**
> However, what still puzzles me is...

...**if**...

```
var **a**=("**123**");
```

...**and**...

```
var **b**=(**a++**);
```

...**how** can the output of...

```
document.write(**a**);
```

...be **124**?

Thanks for any additional thoughts....

Read where I said:

```
a++;
// is the same as
var a = a + 1;
```

```
// so if
var a=("123");
// and...
var b=(a++);
// equals 124

//then,
var b=(a++);
//must also equal
var b = a + 1;
```

```
// also if
var a=("123");
// and...
var b=(a + "1"); // notice the "" around the one
// than it will equal 1231 because JavaScript is running concatenation, not arithmetic
```

---

### Post by solwic on 2008-12-12
> **maclenin said:**
> **banago:**

and

**altonbr:**

Thanks for the clarification(s)!

I think I was clear, for the most part (save for the PHP reference), on the "meaning" of a++, generally (**banago**), and the "syntax" of javascript, more specifically (**altonbr**), re: (a+1) vs. (a+"1") and so forth....

However, what still puzzles me is...

...**if**...

```
var **a**=("**123**");
```

...**and**...

```
var **b**=(**a++**);
```

...**how** can the output of...

```
document.write(**a**);
```

...be **124**?

Thanks for any additional thoughts....

It can't be, can it?  If a = 123 and b=a++, then writing variable a would have nothing to do with the a++ in variable b.

See what I'm saying?  You add 1 to a in assigning variable b, but then you call variable a, which has had nothing added to it.

---

### Post by maclenin on 2008-12-13
**altonbr** and **jrock612**

Thanks to both for the continued reflections....

However, in order for me to make certain I am getting my latest point across, I'd like to suggest that y'all join me in a little experiment:

1. Pop open a simple .txt editor (e.g. mousepad)...

2. Copy and paste the following into the .txt file (NB: nothing malicious here)...

```
<html>
<title>javatest.html</title>
<body>

<script type="text/javascript">

var a=("123");
var b=(a++);

document.write(b + " is the value of var b" + "</br>");
document.write(a + " is the 'curious' value of var a and the basis for my question...." + "</br>");

</script>

</body>
</html>
```

3. Save your new .txt file as, for example, "javatest.html"...

4. Open this new .txt file with your web brower of choice...

5. Observe....

Comments?

---

### Post by altonbr on 2008-12-15
```
<html>
<title>javatest.html</title>
<body>

<script type="text/javascript">

var a=("123");
var b=(a++);
var c=(a + "1");
var d=(a + 1);

document.write("a = " + a + "</br>"); // a = 124
document.write("b = " + b + "</br>"); // b = 123
document.write("c = " + c + "</br>"); // c = 1241
document.write("d = " + d + "</br>"); // d = 125

</script>

</body>
</html>
```

Must say that's pretty weird for variable 'a'. Sorry, I can't tell you what that's called or why that happens but I don't like it.

For PHP,
[PHP]<?php

$a=("123");
$b=(a++); // error here
$c=(a + "1");
$d=(a + 1);

echo('$a = ' + $a + "\n");
echo('$b = ' + $b + "\n");
echo('$c = ' + $c + "\n");
echo('$d = ' + $d + "\n");

?>
[/PHP]
it returns
```
Parse error: syntax error, unexpected T_INC in /home/brett/test.php on line 4
```

---

### Post by maclenin on 2008-12-18
I think I've found the answer...

> Increment (++)

The increment operator is used as follows:
var++ or ++var

This operator increments (adds one to) its operand and returns a value. If used postfix, with operator after operand (for example x++), then it returns the value before incrementing. If used prefix with operator before operand (for example, ++x), then it returns the value after incrementing.

For example, if x is 3, then the statement

y = x++

increments x to 4 and sets y to 3.

If x is 3, then the statement

y = ++x

increments x to 4 and sets y to 4.

...courtesy: [http://lib.ru/JAVA/javascr/expr.html](http://lib.ru/JAVA/javascr/expr.html)

---

