---
title: "compiling error with g77"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by Schjoh on 2007-04-19
Hi

I'm a n00b in linux and fortran, so here is probable a stupid question.
I'm trying to compile a fortran code using g77, so typed, and got:

```
g77 template.f
/usr/bin/ld: crt.0: No such file: No such file or directory
collect2: ld returned 1 exit status
```

It seems like I need some sort of files, but I don't know what files it is. Or is there something else wrong?

---

### Post by LaRoza on 2007-04-19
Move to the Programming Talk forum.

I can't help with Fortran, but people there will.

People in this forum are typically not programmers and will not know what a compiler is.

You might want to make sure the compiler and all of its dependencies are installed and that you are directing the compiler to your source code file.

---

### Post by LaRoza on 2007-04-19
I am assuming that g77 is like g++ in many ways.

Put all of your documents in your Home folder. (/home/username)

To compile a C++ source called template.cpp in my Home folder, I would use:

g++ /home/laroza/template.cpp -o template

(-o in g++ names the resulting binary, laroza is my name here, not my name on my computer)

---

### Post by Schjoh on 2007-04-19
Ok Thanks

---

