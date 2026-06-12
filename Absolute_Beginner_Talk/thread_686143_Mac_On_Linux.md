---
title: "Mac On Linux"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by RadiationHazard on 2008-02-02
Ok, so i'm wanting to run garage band. i've wanted that program forever!! what would be better for running that program Mac on Linux ( [maconlinux.org]("http://maconlinux.org") ) or PearPC ( [pearpc.sourceforge.net]("http://pearpc.sourceforge.net/") ) and can you please give me the easiest way to install these. or give me a how to site or maybe thread that's already on here.

thank you!!!
RadiationHazard

---

### Post by (((X))) on 2008-02-03
Extract downloaded program, then cd to that directory in terminal:
code:
$ ./configure
$ make
Now you need sudo rights:
$ sudo make install
To remove files you created with make(you don´t need):
$ make clean

---

