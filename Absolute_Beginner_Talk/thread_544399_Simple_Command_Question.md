---
title: "Simple Command Question"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2007-09-06
I've been playing around with Ubuntu for a few weeks now and
have seen a few things that I'd like to know more about.

Sometimes when I look at a shout cuts properties, in the 
command box I see the program name then %m or something to
that affect. What does %  mean?

Example: Totem %m

---

### Post by tvrg on 2007-09-06
Where are you seeing that shortcut?
Usually things like that are used to pass parameters to a program (eg the filename of the file you want to open in totem)

---

### Post by hyper_ch on 2007-09-06
hmmm, good question... normally parameter are given directly after the command

e.g.

```

tar xvfz file.tar.gz

```

or they are first initiated with a dash (-) and then the parameter name and then maybe a value

e.g.
```

rm -f file

```

But I don't think I've encountered teh %-sign so far...

---

### Post by dpar on 2007-09-06
From the Beginners Guide to Bash.....


> Table 3&#8722;4. Arithmetic operators
Operator                                             Meaning
VAR++ and VAR&#8722;&#8722;                                      variable post&#8722;increment and post&#8722;decrement
++VAR and &#8722;&#8722;VAR                                      variable pre&#8722;increment and pre&#8722;decrement
 / a&#8722; and +                                              unary minus and plus
! and ~                                              logical and bitwise negation
**                                                   exponentiation
[COLOR="Red"]*,nd %                                           multiplication, division, remainder[/COLOR]
+ and &#8722;                                              addition, subtraction
<< and >>                                            left and right bitwise shifts
<=, >=, < and >                                      comparison operators
== and !=                                            equality and inequality
&                                                    bitwise AND
^                                                    bitwise exclusive OR
|                                                    bitwise OR
&&                                                   logical AND
||                                                   logical OR
expr ? expr : expr                                   conditional evaluation
=, *=, /=, %=, +=, &#8722;=, <<=, >>=, &=, ^= and |= assignments
,                                                    separator between expressions
Shell variables are allowed as operands; parameter expansion is performed before the expression is evaluated.
Within an expression, shell variables may also be referenced by name without using the parameter expansion
syntax. The value of a variable is evaluated as an arithmetic expression when it is referenced. A shell variable
need not have its integer attribute turned on to be used in an expression.



Sorry, the formatting is'nt the way it was in the manual.

---

### Post by Harpoon on 2007-09-06
When confronted with something like this, a search for "linux commands" and sometimes "unix commands" gives you some good references.  Here are two of them, but neither seems to include "%" which sounds like part of a script rather than a command, per se:

[http://www.debianhelp.co.uk/commands.htm](http://www.debianhelp.co.uk/commands.htm)
[http://www.computerhope.com/unix.htm](http://www.computerhope.com/unix.htm)

---

### Post by Steve1961 on 2007-09-06
Mmm...  I've wondered about this myself.  Under the removable drivers and media menu there's definitely a default entry of:

Totem %m

for dvds and:

sound-juicer -d %d

for audio cds

---

### Post by WebSiteGuru on 2007-09-06
Same questiobn here. I had been wondering what it was for.

---

### Post by tvrg on 2007-09-06
the %m etc signs are substituded.

Eg: if you see totem %s or something in a right click action, it's probably subsituted by the filename you clicked on

---

### Post by FuturePilot on 2007-09-06
I've been wondering the same thing. If you look at the menu entry for Firefox the command is this
```
firefox %u
```

---

### Post by tvrg on 2007-09-06
> **FuturePilot said:**
> I've been wondering the same thing. If you look at the menu entry for Firefox the command is this
```
firefox %u
```

In firefox the %u gets replaced by the url

for example, try dragging a file onto the firefox icon. the file wil open in firefox
the %parameters get replaced by something from the context

---

### Post by tvrg on 2007-09-06
Ha!

finally found the list:
[https://help.ubuntu.com/7.04/user-guide/C/launchers.html](https://help.ubuntu.com/7.04/user-guide/C/launchers.html)

---

