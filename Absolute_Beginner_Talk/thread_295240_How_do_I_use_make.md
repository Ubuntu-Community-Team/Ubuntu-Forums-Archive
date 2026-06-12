---
title: "How do I use make"
date: 2006-11-07
forum: Absolute Beginner Talk
---

### Post by bdb51 on 2006-11-07
I'm not a new user of ubuntu. Ever since I installed Ubuntu I haven't been able to use the "make" and "make install" commands. I've tried to install many packages but when I reach the the part that I have to use make, it tells methat it can't find make.

CAN ANYBODY HELP ME

---

### Post by bruenig on 2006-11-07
```
sudo apt-get install build-essential
```
That should get you all that you need to compile including make and make install.
If you don't mind my inquiry, what is it that you are compiling? It may exist in the repos and is far easier to install through the repos.

---

### Post by sethmahoney on 2006-11-07
Applications->Accessories->Terminal

In the terminal, type

sudo apt-get install build-essential

That should get you started.

Oh, yeah, like the previous poster said, you should always check the repositories before installing from source files.  Go to the System Menu, and look for Synaptic Package Manager in there.  It should have most of what you might need.

---

### Post by Aualin on 2006-11-07
try with
sudo apt-get install make
and then try the make commands ;)

---

### Post by Aualin on 2006-11-07
lol, you guys are fast!

---

### Post by sethmahoney on 2006-11-07
> **Aualin said:**
> lol, you guys are fast!

Heh, I know!  I was all excited that there was finally a tech support type question I could answer, but someone beat me to it!

---

