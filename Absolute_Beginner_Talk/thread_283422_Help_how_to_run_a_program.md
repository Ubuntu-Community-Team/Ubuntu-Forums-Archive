---
title: "Help how to run a program"
date: 2006-10-24
forum: Absolute Beginner Talk
---

### Post by mattgaunt on 2006-10-24
Hey guys

Ive just written a program and compiled

When using the uni Computers, running redhat, i can jus compile it in a terminal, type the name of the compiled file and it runs it in the terminal, does anyone know what i need to type to get my program to run in a terminal? because its compiled and i just need to see the value it comes out with, its a crappy program just to do a simple calculation

So anyway any help would be great

Thanks alot

---

### Post by Arndt on 2006-10-24
> **mattgaunt said:**
> Hey guys

Ive just written a program and compiled

When using the uni Computers, running redhat, i can jus compile it in a terminal, type the name of the compiled file and it runs it in the terminal, does anyone know what i need to type to get my program to run in a terminal? because its compiled and i just need to see the value it comes out with, its a crappy program just to do a simple calculation

So anyway any help would be great

Thanks alot

If the program is called 'prog' and is in the current directory, just type
```

./prog
```

It sounds like you have '.' (the current directory) in your PATH variable at the uni, and not where you are now. Do

```
echo $PATH
```

if you want to check.

---

