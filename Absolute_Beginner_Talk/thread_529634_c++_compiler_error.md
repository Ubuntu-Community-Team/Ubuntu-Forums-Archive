---
title: "c++ compiler error"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by damansandhu on 2007-08-19
hi , i am using kubuntyu 7.04 and i am getting this error when i try to run GNU C Compiler.

daman@Ultimate:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree
Reading state information... Done
build-essential is already the newest version.
The following packages were automatically installed and are no longer required:
libberylsettings0-gconf
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
daman@Ultimate:~$ gcc
gcc: no input files
daman@Ultimate:~$

---

### Post by jamvegan on 2007-08-19
What are you trying to compile?  gcc requires, at minimum, that you follow the command with the name of the source file you wish to compile, and there are many other options that you might wish to include.  Also, if the source code is C++, you may get better performance using g++ rather than gcc.  It calls the same compiler, but with C++ defaults.

You can read gcc's documentation by typing
```
man gcc
```
Or, if that's not clear to you (it's not clear to me) there's a good book available for free online: [An Introduction to GCC]("http://www.network-theory.co.uk/docs/gccintro/").

---

### Post by damansandhu on 2007-08-19
i just want to write some basic c++ programs , arrays , pointers etc , i do some of it in windows , i am new in linux i dont know how to start program . 

can you plz tell me where should i write such things like
#include<conio.h>
stuff like this

---

### Post by jamvegan on 2007-08-19
This is kind of a big topic. :-)

The book that I linked to above has good clear examples.  For instance, you might want to look at this chapter: [Compiling multiple source files]("http://www.network-theory.co.uk/docs/gccintro/gccintro_11.html").

---

### Post by sumguy231 on 2007-08-19
> can you plz tell me where should i write such things like
Eh? The same rules still apply for #include and other preprocessor directives, you just can't expect to use Windows libraries. There's probably plenty of tutorials on basics of developing for Linux, ask Google.

By the way, if you end up doing any actual projects, you might want to look into a full IDE like Eclipse or KDevelop.

---

### Post by TheWizzard on 2007-08-19
you can use a text editor like gedit or kate to write sourcecode. 

then use gcc to compile it into a binary. gcc is just the compiler. nothing more.

---

