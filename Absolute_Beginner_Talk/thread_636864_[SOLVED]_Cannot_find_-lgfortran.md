---
title: "[SOLVED] Cannot find -lgfortran"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by rockballad on 2007-12-10
Hi,

I've installed gfortran, and actually, I'm able to compile a .f file using gfortran at commandline. But when I compile with gcc and need gfortran library, this command doesn't work:

gcc test.c  -lgfortran

I did a search and found libgfortran.a, libgfortran.so at /usr/lib/gcc/x86_64-linux-gnu/4.2
but don't know how to make it understand about -lgfortran.

Could you tell me how to do that, please? Thanks in advance.

---

### Post by pointone on 2007-12-10
[http://gcc.gnu.org/wiki/GFortranUsage](http://gcc.gnu.org/wiki/GFortranUsage)

---

### Post by rockballad on 2007-12-10
Thanks, pointone, for the good link. I'll read it right now.

---

### Post by rockballad on 2007-12-10
OK, I got it. Just add the Link dir, like this:

gcc -c   test.c -o test.o  -L/usr/lib/gcc/x86_64-linux-gnu/4.2.1

/usr/lib/gcc/x86_64-linux-gnu/4.2.1 contains libgfortran you see.

Thanks, and have a nice day!

---

