---
title: "Gcc build error"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by noorez on 2007-02-24
I was attempting to build the gcc source files but i received this error message:

gcc: gengtype-lex.c: No such file or directory
gcc: no input files
make[3]: *** [build/gengtype-lex.o] Error 1
make[3]: Leaving directory `/home/noorez/Desktop/objdir/gcc'
make[2]: *** [all-stage1-gcc] Error 2
make[2]: Leaving directory `/home/noorez/Desktop/objdir'
make[1]: *** [stage1-bubble] Error 2
make[1]: Leaving directory `/home/noorez/Desktop/objdir'
make: *** [all] Error 2


I download the source using
svn -q checkout svn://gcc.gnu.org/svn/gcc/trunk gcc so I shouldn't be missing any files. Can someone tell me what might be wrong?

---

### Post by apjone on 2007-02-24
why not install gcc from synaptic /apt ?

---

### Post by Perfect Storm on 2007-02-24
```
sudo aptitude install build-essential
```
will get you the basic tools for compiling.

---

