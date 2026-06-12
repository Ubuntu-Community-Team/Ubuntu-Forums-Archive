---
title: "Newbie"
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by garyplais on 2006-07-20
I just installed Ubuntu 6 this morning for the first time.  After I restart my PC I get this error "The Greetor application appears to be crashing. Attempting to use a different one."  After I clear it I do get to another screen that allows me to login to my desktop, but it is rather annoying.  any idea's on what could cause this and an easy way to fix it?
Thanks in advance for any assistance.
:confused:

---

### Post by monkieie on 2006-07-20
> **garyplais said:**
> I just installed Ubuntu 6 this morning for the first time.  After I restart my PC I get this error "The Greetor application appears to be crashing. Attempting to use a different one."  After I clear it I do get to another screen that allows me to login to my desktop, but it is rather annoying.  any idea's on what could cause this and an easy way to fix it?
Thanks in advance for any assistance.
:confused:

Good question - hbeing still in my first linux week I can't say that I've come across that one yet. Have you run the updates once the desktop is loaded? Perhaps that might fix it. On the other hand, I'm sure that some clever person here will know the solution to it ;)

---

### Post by garyplais on 2006-07-20
Just installed all of the updates available and still have the error.  Be nice to hear from some experienced users!!!:confused:

---

### Post by T700 on 2006-07-20
This seems to be a fairly random bug that has been [reported]("https://launchpad.net/distros/ubuntu/+source/gdm/+bug/48936ce/gdm/+bug/48936") and is being investigated.  Sadly, there is no good, consistent, fix, short of reinstalling or installing KDE and using the display manager for that (you can still run the Gnome desktop).

Some people have reported the following fixed the problem:

```
wget http://archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/libgtk2.0-0_2.8.13-1ubuntu1_i386.deb
dpkg -i libgtk2.0-0_2.8.13-1ubuntu1_i386.deb
``` 
but I have no first hand knowledge of it--*use at your own risk!*  It looks safe, but I haven't tried it.

Good luck,
Paul

---

