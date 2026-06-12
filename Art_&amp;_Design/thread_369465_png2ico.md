---
title: "png2ico"
date: 2007-02-24
forum: Art &amp; Design
---

### Post by adamthompson on 2007-02-24
Does anyone know how to install png2ico in Ubuntu? I got the following error when I tried to make:

g++ -W -Wall -O2 -finline-functions -g -o png2ico png2ico.cpp -lpng -lz -lm
make: g++: Command not found
make: *** [png2ico] Error 127

---

### Post by Stemp on 2007-02-24
You don't have the c++ compiler.
So install **g++** package or **build-essential**

---

### Post by musicinmybrain on 2007-12-19
Another caveat for compiling [png2ico](http://www.winterdrache.de/freeware/png2ico/index.html) is that you must have the libpng headers installed (libpng12-dev). The errors you will see if you do not are relatively cryptic. Once you have compiled png2ico, you will have to put the executable someplace sensible in the path. For example: ```
sudo cp png2ico /usr/local/bin
```

You might also be interested in the package icoutils in the repositories, which provides icotool wand wrestool.

---

### Post by AmpersUK on 2011-03-08
Useful program, I'm amazed it isn't in the Ubuntu repository.

---

