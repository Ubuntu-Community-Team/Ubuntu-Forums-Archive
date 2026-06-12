---
title: "Compiling program that uses plplot"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by browny254 on 2008-02-16
Hi, I posted this in Programming/Compiling forum about 12 horus ago but it has just sat at the top of the forum with no replies so i was hoping to put it here because it seems a few more ppl look and it is a beginners question too i think...ok...

Im trying to compile some c++ code that uses a couple of functions of plplot but not sure exactly how to do it.

I have included plplot.h at the beginning of my code (which i found a mention to in the documentation somewhere) and use -lplplot when i go to compile, but i get error: plplot.h: No such file or directory.

Im not sure how im ment to do it correctly or if i have even installed the plplot libraries correctly (im still really new to this so i just ticked everything that mentioned plplot in the synaptic package manager...)


thanks for any help you can give.

---

### Post by peabody on 2008-02-16
I just installed the libplplot-dev package.  It appears that the plplot file you want is at /usr/include/plplot/plplot.h

Which means the include directive should probably look like this,

#include <plplot/plplot.h>

Let me know if that works or not.

---

### Post by PeterJS on 2008-02-16
```

peter@Osirus:~$ apt-file search plplot.h
drscheme: usr/lib/plt/collects/plot/src/all/plplot.h
libplplot-dev: usr/include/plplot/plplot.h
plplot-doc: usr/share/doc/plplot-doc/html/acquiring-plplot.html

```

I'm betting it's the middle one, do you have that package installed? Generally when compiling things yourself you want to install the -dev packages for things.

---

### Post by browny254 on 2008-02-16
Thanks for the replies guys,

peabody - yeah that was it, thanks

PeterJS - i got the same output as you there so i guess i have them.


now im not exactly sure how i go about compiling my program, this is what i did, im assuming that i have to do something else instead of -lplplot

```
$ g++ histoplot.cpp -lgsl -lgslcblas -lplplot -o histoplot
/usr/bin/ld: cannot find -lplplot
collect2: ld returned 1 exit status

```

---

### Post by browny254 on 2008-02-16
ok i tried something different but am still getting a compile error...i may be doing it all wrong because im not really that confident with it yet

```
$ g++ histoplot.cpp -Iplplot -o histoplot
/tmp/ccZI60Hr.o: In function `main':
histoplot.cpp:(.text+0x23e): undefined reference to `c_plinit'
histoplot.cpp:(.text+0x278): undefined reference to `c_plhist'
histoplot.cpp:(.text+0x27d): undefined reference to `c_plend'
collect2: ld returned 1 exit status
```

any thoughts?

---

### Post by peabody on 2008-02-16
couple things...that should be -l (el) not -I (eye) and the library looks to be named plplotd

---

### Post by browny254 on 2008-02-16
plplotd...damn, i cant beleive it was that easy.

how can i tell what the library is named? this seems to be almost the biggest problem i have when trying to compile stuff?

---

### Post by peabody on 2008-02-16
If you know the dpkg name of an installed library the absolute best way is to dpkg -L name and see which files are directly under /usr/lib and ending in .so.#.#.# (# version numbers).  The name will be the name after the 'lib' part, but before the filename suffix.

If you're ever on a machine where you don't have the luxury of dpkg, you can just poke around /usr/lib.

---

