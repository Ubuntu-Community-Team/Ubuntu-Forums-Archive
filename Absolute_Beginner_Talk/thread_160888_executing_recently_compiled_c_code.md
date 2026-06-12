---
title: "executing recently compiled c code"
date: 2006-04-15
forum: Absolute Beginner Talk
---

### Post by qiemem on 2006-04-15
So I just compiled some c code using gcc, but I can't seem to figure out how to execute it from the terminal. I tried "exec [directory]/program" but it just closed the terminal. How do I do it? Sorry if this is a really dumb question and I'm missing something completely obvious.

---

### Post by mscman on 2006-04-15
you should just be able to type the name of the output file.  For example, the default output of a compiled program is 'a.out' in the same directory.  To execute (assuming you're in the same directory as the program), you would simply type
```
./a.out
```
If the program is in a different directory, you would simply replace the '.' with the path to the file.

---

### Post by dabear on 2006-04-15
[QUOTE=qiemem]So I just compiled some c code using gcc, but I can't seem to figure out how to execute it from the terminal. I tried "exec [directory]/program" but it just closed the terminal. How do I do it? Sorry if this is a really dumb question and I'm missing something completely obvious.[/QUOTE]
Well, compiled sources should be made directly executable by the compiler. If the name of the program for example is a.out, you just do a:
```

./a.out

```
That is, prepend «./» to the file name

---

### Post by qiemem on 2006-04-15
Doh! I forgot the "./". I just typed the program name. I'm an idiot...

Thanks!

---

