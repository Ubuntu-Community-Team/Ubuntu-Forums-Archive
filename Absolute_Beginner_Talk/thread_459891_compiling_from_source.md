---
title: "compiling from source"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by xtang on 2007-05-31
I never really understood what the "./configure" command actually does when you compile something. Does it read some file called configure or something?

---

### Post by plcdfa on 2007-05-31
No, it examines your system and decides how the program should be compiled on your machine. It writes these into a Makefile, which will be read by the make program.

---

### Post by plcdfa on 2007-05-31
Uh, well in fact the command ./configure really runs a script file called configure from the current directory, of course. It does what I wrote above.

---

