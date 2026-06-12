---
title: "c compiler"
date: 2006-08-21
forum: Absolute Beginner Talk
---

### Post by oscar78 on 2006-08-21
I am trying to comile a c file I wrote in emacs.  In the terminal i used "cc <file>" as common on unix systems, but I guess that commmand doesn't exist in linux os.  Does anyone know the command to compile an emacs program written in c?

---

### Post by kostkon on 2006-08-21
In Linux we have [GCC]("http://en.wikipedia.org/wiki/GNU_Compiler_Collection") and not CC.

If you install the build-essential package by just doing

```
sudo apt-get install build-essential
```

on a terminal or through Synaptic, then you will be able to compile your C code like that:

```
gcc -o test test.c
```

etc. etc.

You can also use an IDE if you like; there is a [list of IDEs in the Ubuntu documentation]("https://help.ubuntu.com/ubuntu/desktopguide/C/programming.html").

---

### Post by oscar78 on 2006-08-21
for some reason, though, build essential doesnt seem to be accessable through the terminal or  synaptic

---

### Post by IYY on 2006-08-21
What's the output of:

```
sudo apt-get install build-essential
```

---

### Post by Ragazzo on 2006-08-21
cc is a symbolic link to GCC by default. You can change it with "sudo update-alternatives --config cc".

---

