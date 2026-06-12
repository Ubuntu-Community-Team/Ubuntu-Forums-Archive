---
title: "Building GCC 3.0.4 from source"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by anothrguitarist on 2008-02-01
The other day, I posted about running an old version of GCC, but I am haivng trouble installing it.

Heres what I did

created the directory, objdir
$ sudo ./configure
$ cd ../objdir
$ sudo make bootstrap

But I received the following error after entering sudo make bootstrap:
make[2]: *** No rule to make target `../zlib/libz.a', needed by `jar'.  Stop.
make[2]: Leaving directory `/home/john/gcc3/objdir/fastjar'
make[1]: *** [all-fastjar] Error 2
make[1]: Leaving directory `/home/john/gcc3/objdir'
make: *** [bootstrap] Error 2

Does anyone know what the error means and how to fix it?

---

### Post by mattismyname on 2008-02-01
Sounds like you might need zlib.

sudo apt-get install zlib-dev

---

### Post by anothrguitarist on 2008-02-01
Hmmm, it's not finding zlib-dev, but I looked in synaptic and I have zlib1g-dev.

EDIT: Is is possible my sources.list is not correct?

---

