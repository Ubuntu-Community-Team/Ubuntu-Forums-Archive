---
title: "problems with the shell"
date: 2006-10-26
forum: Absolute Beginner Talk
---

### Post by mandos on 2006-10-26
it feels imposible to me to asign a new value using sums to a variable 

i've tried (being x the variable)
x=expr 1 + 1
but it didn't work

does anyone know how to do it?
thank you

---

### Post by Arndt on 2006-10-26
> **mandos said:**
> it feels imposible to me to asign a new value using sums to a variable 

i've tried (being x the variable)
x=expr 1 + 1
but it didn't work

does anyone know how to do it?
thank you

To use the output from a program as part of a string in a shell, use back quotes:

```
$ x=`expr 1 + 1`
$ echo $x
2
```

What your command does is try to run the command "1 + 1", and while doing so letting the variable x be "expr".

---

