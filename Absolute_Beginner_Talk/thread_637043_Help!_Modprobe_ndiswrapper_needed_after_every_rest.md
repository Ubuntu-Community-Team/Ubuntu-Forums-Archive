---
title: "Help! Modprobe ndiswrapper needed after every restart."
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by westyonfire on 2007-12-10
Hi everyone,
I've been on ubuntu for a few weeks now and i love it. Every pc in the house now has an ubuntu partion. Dad and brothers weren't too impressed I'd 'ubuntufied' their computers...but that soon changed. ubuntu is now their OS of choice too. anyway, the problem: I have to modprobe ndiswrapper every time i restart my pc for some reason. I don't know how to make the ndiswrapper and my wireless work permanently. Can anyone help me out please?

thanks in advance :biggrin:

---

### Post by skrribble on 2007-12-10
you need to add ndiswrapper to a blank line in your /etc/modules file

open up a terminal and do 
```
gksudo gedit /etc/modules

```
and then add the word ndiswrapper to a blank line.  your file should look something like
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

ndiswrapper
```

it might also have some other modules on there that load at startup

---

### Post by westyonfire on 2007-12-10
it worked! thank you soo much. I assume I have to do this every time i want a programme to initiate on startup?

---

### Post by skrribble on 2007-12-10
you are very welcome..... this only needs to be done with modules you want to load on startup.  modules are kind of like drivers, so you don't need to put programs in /etc/modules.

if you want programs to load on startup, go to system>preferences>sessions and add your programs there

---

