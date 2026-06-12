---
title: "Hmm, what am I doing wrong? Compiling from Source"
date: 2006-11-13
forum: Absolute Beginner Talk
---

### Post by MicroChris on 2006-11-13
I'm trying to install an m4a plugin for XMMS, but when I try to install from source, this is what I get:

```
chris@chris-desktop:~/Desktop$ cd xmms-mp4_20050213
chris@chris-desktop:~/Desktop/xmms-mp4_20050213$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables

```

What do I need to install?

Thanks!

---

### Post by K.Mandla on 2006-11-13
Is this not an option for you?

*sudo aptitude install xmms-mp4*

I have no problems playing m4a's with that, but perhaps you are working with something different.

---

### Post by MicroChris on 2006-11-13
Lol, that did the trick.. I searched Synaptic for M4A plugins, I guess the correct term is MP4.

Just so this issue doesn't come up in the future, am I missing a C compiler or any other program?

---

### Post by taurus on 2006-11-13
And don't forget to install the build-essential package if you plan to build anything from source!!!

```
sudo aptitude update
sudo aptitude install build-essential
```

---

