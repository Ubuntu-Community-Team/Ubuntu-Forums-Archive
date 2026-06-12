---
title: "quick gcc question"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by xboxbman on 2007-03-17
i'm trying to compile a .c program, but get a mess of errors, i'm assuming because i'm not calling on the rights libraries when I compile it.  I know when compiling code with #include <math.h> at the top, I need to write -lm in the gcc command i.e : ```
gcc example.c -o example -lm
```.  I'm assuming i need to add something to the gcc command for the following, but don't know what call on.

#include <stdio.h>
#include <string.h>
#include <time.h>
#include "ecma-267.h

any help would be great

---

### Post by Henry Rayker on 2007-03-17
I'm not sure on the others, but, due to the syntax, I believe the ecma-267.h file should be something you're providing...it should be in the directory you are compiling from (aka, the working directory)

---

### Post by dstew on 2007-03-17
Is this a program you have written yourself? Is it a sourceforge download that came in a .tar.gz package?

The include statements should be part of the program code.

Have you installed build-essentials?

---

