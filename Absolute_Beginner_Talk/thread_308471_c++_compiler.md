---
title: "c++ compiler"
date: 2006-11-28
forum: Absolute Beginner Talk
---

### Post by nite owl on 2006-11-28
Hi just wondering if anyone could point me in the direction or name a good c++ compiler for Linux as I'm having abit of trouble finding one...Or maybe is there one already built into Ubuntu like there is one for Python???? Im on 6.06 LTS

---

### Post by Stian24 on 2006-11-28
There is a g++ that is the gnu c++ compiler you can find it in repos so just search for it in synaptic.

---

### Post by Bachstelze on 2006-11-28
There is no such thing as a Python compiler. Python is an interpreted language.

To get gcc, the GNU C Compiler, do 

```
sudo apt-get install build-essential
```

---

### Post by nite owl on 2006-11-28
HI I used the line *'sudo apt-get install build-essential'*...it worked and its installed
.....anyway how do i access the compiler now???? Im confused lol sorry

---

### Post by Bachstelze on 2006-11-28
*man gcc* ;)

---

### Post by LLRNR on 2006-11-28
If you want to compile a source file called *example.cpp* then you'd have to say:
```
gcc -o example example.cpp
```
If you use gcc without "-o" (something like "gcc example.cpp") then the executable that comes out of the process of compilation will be called by default *a.out*.

There are a lot of other options for gcc, just check out the man pages.

LLRNR

---

### Post by mrphd on 2006-11-28
Depending upon what you intend to use the compiler for, you might also want to consider the Intel C++ compiler which is available free for non-commercial use for Linux from their website.

---

