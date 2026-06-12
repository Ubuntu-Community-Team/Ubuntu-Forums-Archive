---
title: "scripts are hard"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by sloop on 2007-10-18
Hi to you ubuntu friends.I'm very new with Ubuntu and now I try to write scripts.This is the simple thing -  if expr A=B; then  echo eqv; else echo no eqv; fi.When I run this I always get  
'eqv' (if A=1 and B=1/ or A=1 and B=2).Why is that?

---

### Post by ronald.higgins on 2007-10-18
Not quite sure what you're trying to achieve, something like below ?

```

#!/bin/bash
A=1
B=2
if [ $A = $B ]
        then
                echo "All things are equal";
        else
                echo "All things are not equal";
fi

```

---

### Post by tkharris on 2007-10-18
> **ronald.higgins said:**
> Not quite sure what you're trying to achieve, something like below ?

```

#!/bin/bash
A=1
B=2
if [ $A = $B ]
        then
                echo "All things are equal";
        else
                echo "All things are not equal";
fi

```


That should be:

```

if [ $A -eq $B ]

```

= ( better written == ) is for string comparisons, where -eq and -ne are for numerical comparison.

---

### Post by bigboy_pdb on 2007-10-18
There should also be quotes around $A and $B in case the variables contain whitespace or newlines. So it should be:
```

if [ "$A" -eq "$B" ]

```

The reason why "expr A=B" does not work is because the command "expr" expects three arguments. The first thing that will be compared, the type of comparison, and the second thing that the first thing will be compared to. They don't always come in that order. Read the man page (using the command "man expr") to understand why.

You only provided one argument "A=B" to make it three arguments you need to add spaces on either side of the equal sign. So it would become "A = B". This new expression would work but it wouldn't do what you want it to do because you're always asking if the character "A" equals the character "B" (and they are never equal). You want to access the variables that you called A and B. To do this you must use $A and $B. I mentioned that quotes should be added around $A and $B because if you don't add them then there could be more than 3 arguments. For example when A="hello there" and B="you", the command "expr $A = $B" is the same as "expr hello there = you" meaning there are four arguments (argument one is hello, two is there, three is =, and four is you). When you use quotes, 'expr "$A" = "$B"' becomes 'expr "hello there" = "you"' meaning there are three arguments (argument one is "hello there", two is =, and three is "you").

---

### Post by sloop on 2007-10-19
Thank you this works. But tell me if you can where I can read about such operators and other things about scripts for my level.

---

### Post by dj Kalma on 2007-10-19
> **sloop said:**
> Thank you this works. But tell me if you can where I can read about such operators and other things about scripts for my level.

[http://www.freeos.com/guides/lsst/](http://www.freeos.com/guides/lsst/)

---

### Post by sloop on 2007-10-19
Thank you:)

---

### Post by bigboy_pdb on 2007-10-20
There are a number of good guides for a variety of things on the Linux Documentation Project's website.

They can be found here:
[http://tldp.org/guides.html](http://tldp.org/guides.html)

You might want to look at "Introduction to Linux - A Hands on Guide" for a good overview of some concepts that most people should know regarding Linux OSes. The "GNU/Linux Command-Line Tools Summary" is also worth taking a look at. Regarding scripting, there are two guides that would be useful: the "Bash Guide for Beginners" and the "Advanced Bash-Scripting Guide". The "Bash Guide for Beginners" teaches you how to script using the bash shell. The "Advanced Bash-Scripting Guide" is more of a reference manual than an advanced scripting guide.

---

