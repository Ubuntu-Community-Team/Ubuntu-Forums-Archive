---
title: "compiling C"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by muchane on 2008-01-11
Why am I not able to compile C code on the Gutsy ? I keep getting a'file not found' error message even when I explicitly state the path of  the file? And speaking of paths, when I add the path of my sqlite3 bin directory in the .bashrc it doesn't work.

---

### Post by Joeb454 on 2008-01-11
what path are you putting into gcc?

---

### Post by yabbadabbadont on 2008-01-11
Since you didn't say, I'll ask the obvious question.  Do you have the build-essentials package installed?

---

### Post by Joeb454 on 2008-01-11
Good point that also helps :p

The code to compile a C program would be something like 

```
gcc /home/joe/c/myfile.c -o myfile
```

The first part - /home/joe/c/myfile.c - is the path to where the file is on your system

---

