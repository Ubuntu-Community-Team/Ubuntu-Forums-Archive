---
title: "How do they, in some blogs, auto convert vertical quotation marks into curly ones?"
date: 2011-06-03
forum: Art &amp; Design
---

### Post by vezolmi on 2011-06-03
In many blogs, if you write, for example,  a comment like this:
> I like your "superb" idea.When you submit it it appears as:
> I like your “superb” idea.The typewriter (vertical, straight) quotation marks are automatically replaced by typographic (curly) ones.

How do they do it? With PHP, JavaScript or CSS perhaps?

Regards

---

### Post by BobSongs on 2011-06-03
I cannot answer your question simply because I've never seen a board or forum where " " that style of quotation mark was converted to a type-set sort, the ones that look like 66 99.

The problem is: many of us have grown accustomed to inch-marks-for-quotes when reading text online. I prefer 66 99 when typesetting a document. It looks more professional that " or ' .

---

### Post by vezolmi on 2011-06-05
Thanks. I've seen several blogs or websites where this happens. For example one very related to this one. You can see and test it in a test page they have: [http://www.ubuntugeek.com/test.html](http://www.ubuntugeek.com/test.html)

After searching and testing I've got a PHP example code that does it:

[PHP]
<?php
function doitwell($text)
{
$original=array(' "', '" ');
$replaced=array(' “', '” ');
return str_replace($original,$replaced,$text);
}

$tryitnow = doitwell('We "see" if "it" works or not');
echo $tryitnow;
?>
[/PHP]But the code in the linked site seems to a bit more complex: sometimes converts the vertical quotes into primes instead of curly quotes. I don't know why or when does it (nor the code; but I'm gonna ask; perhaps they can tell us).

---

### Post by vezolmi on 2011-06-05
The problem of those blogs is that if what you submit is a computer code normally you have to reconvert the quotation marks into vertical ones so the code works (the programming languages normally fail with curly quotes; the vertical quotes are usually used to delimit strings).

---

