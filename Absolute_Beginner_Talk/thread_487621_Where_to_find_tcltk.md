---
title: "Where to find tcl/tk?"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by infolasalle on 2007-06-29
Hello,

Newbie question here:

 need to compile a driver for a piece of hardware on my PC with Ubuntu 7.04.  During the initial "make new", the script terminates with error, saying it cannot find "tcl/tk" ???

I looked through available packages to install it, but can't seem to see it anywhere...

Anyone can point me in the right direction please?

Thnaks!

---

### Post by aeiah on 2007-06-29
im on a windows pc at work right now, but i installed tcl and tk last night for some old audio processing software. it should be available in the repositories. have you got universe etc enabled in your sources.list?

---

### Post by Seisen on 2007-06-29
Try this
```
sudo apt-get install tcl8.3 tcl8.3-dev
``` in the terminal

---

### Post by infolasalle on 2007-06-29
@ Seisen / Aeiah:  I was using Ubuntu 7.04 and noticed my driver was recommended for 6.06. Since I am test driving the whole thing, I reinstalled from scratch using the 6.06 LTS release. 

I proceeded to do what Seisen suggested and manually installed the tcl/tk packages. Now, I am getting a different error.

When I go in the directory where the decompress files are located, the instructions tell me to "sudo -s" and then do "make new".   Going "sudo -s" brings me the "root" shell symbol (#). I am assuming this portion works fine. 

When I do "make new", I get "bash : make : command not found"

Any hints?

---

