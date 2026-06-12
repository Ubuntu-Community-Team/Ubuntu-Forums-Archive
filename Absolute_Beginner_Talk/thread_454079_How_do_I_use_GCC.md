---
title: "How do I use GCC?"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by flyguido on 2007-05-25
I'm trying to compile code into a program.  But I don't know anything about programming!

A friend told me I need "GCC" but I couldn't find it under Applications->Add/Remove.  He suggested trying "apt-get" but I can't find that either.

I tried downloading GCC from a mirror but couldn't get it to install.

Is there a simple way to access GCC or a similar application to turn simple code into simple programs?

---

### Post by ewankho on 2007-05-25
Try to go to the command line and type 'gcc'. Also, try the man pages, at the command line type 'man gcc'

---

### Post by spin2cool on 2007-05-25
What kind of simple code?  GCC is a C compiler.  If you have written a program in C, then yes, you can use gcc to compile it.

From the command line:
```
sudo apt-get install gcc
```

Then, 
```
gcc -o outfilename yourCfile.c 
```

---

### Post by flyguido on 2007-05-25
Awesome that works, thanks.  I knew it would be something simple and easy!

---

### Post by madmetal on 2007-05-25
man gcc 
;)
its usefull and its better when you fully new the commands you use..
furthermore you may find things you dont know they exist..

---

