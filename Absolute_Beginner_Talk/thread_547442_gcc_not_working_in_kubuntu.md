---
title: "gcc not working in kubuntu"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by bdsatish on 2007-09-10
HI,
     I did a fresh install of kubuntu last week.

I wrote a simple hello world program in C.

I tried to compile:
[bash]$ gcc hello.c

I got an error:
Cannot find crt1.o : No such file or directory

What's wrong ?

---

### Post by dwhitney67 on 2007-09-10
Try installing gcc.

[FONT="Courier New"]$ sudo apt-get install build-essential[/FONT]

Note if the command above fails, then try with "build-essentials"

---

