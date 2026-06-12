---
title: "how to get this lib? libimf.so"
date: 2006-05-15
forum: Absolute Beginner Talk
---

### Post by neelabhro on 2006-05-15
I'm missing this lib.

./cfg_maker: error while loading shared libraries: libimf.so: cannot open shared object file: No such file or directory


can't seem to get it via apt-get...any ideas?

---

### Post by easyease on 2006-05-15
erm....what package  do you need it for?

---

### Post by Jagot on 2006-05-15
Looks like it's related to compilers, so you could try:

```
sudo aptitude install build-essential
```

Or indeed obtain it using Synaptic.

---

### Post by neelabhro on 2006-05-15
i'm just trying to run a script someone gacve me and the error comes up

---

### Post by richbarna on 2006-05-15
What does the script do? or what is it for?
Is it a "./configure, make,sudo make install" script or just a program?
Also what language is it written in?

---

### Post by neelabhro on 2006-05-15
It is used to convert .xyz to .png image formats i use it with some simulation work I'm doing. I use atomeye which uses .png..or at least is not compatible with .xyz which is the graphical output of the simulator. The script helps with this.

---

### Post by neelabhro on 2006-05-15
I am not sure of the language but i believe it is in Perl

---

