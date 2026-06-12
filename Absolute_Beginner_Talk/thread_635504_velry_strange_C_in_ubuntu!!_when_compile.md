---
title: "velry strange C in ubuntu!! when compile"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by pmn.blazer on 2007-12-08
when i write C program...output is ok....
and I type gcc -o filename without .c filename with ,c
so strange output it..
then i type emacs filename.c&
so strange letter...what is that??pls tell me

---

### Post by llamakc on 2007-12-08
Huh? Explain it again please.

---

### Post by Hospadar on 2007-12-08
Could you post exactly what strange output you are getting, also (if you can) could you post the code you are trying to compile (just attatch the source file)

---

### Post by pmn.blazer on 2007-12-08
my chaning source code like that

---

### Post by croto on 2007-12-08
Hey,

Try this: type in your code using your favorite text editor, save it as test.c. Now type the following in a terminal:
```

gcc -o test test.c

```

That line will compile your code and create an executable file called test. The source code should still be in test.c

EDIT: make sure you don't add any extra space.

---

### Post by llamakc on 2007-12-08
> **pmn.blazer said:**
> my chaning source code like that

You opened the binary in emacs. Don't do that.

---

