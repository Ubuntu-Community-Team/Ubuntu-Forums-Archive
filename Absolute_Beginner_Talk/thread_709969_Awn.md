---
title: "Awn"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by cartisdm on 2008-02-27
So I know AWN is in beta but still.....it crashes all the time for me.  On average it crashes once a day, sometimes more.  I notice it most when I leave my computer for an hour or two then come back to it it's either gone (the dock) or it just frozen.  The rest of ubuntu works but the AWN dock is stuck.  It's a real pain because I don't have a taskbar, system tray, or anything, I run it all from the dock.:confused:

---

### Post by glennric on 2008-02-27
What version of awn are you running?  I rarely have any issues with it.  I have troubles with compiz crashing, but rarely awn.

---

### Post by cartisdm on 2008-02-28
I looked all over the darn thing, where can I find what version it is?

---

### Post by nilarimogard on 2008-02-28
I was having the same problem. Now i use kiba-doc, it doesn't seem to crash.

---

### Post by rolnics on 2008-02-28
I'd forgotten it was beta, no wonder I get lines and stuff!!

Have you tried looking in synaptic to find the version?? I'm not a linux machine so can't try it myself, but I remember coming across details somewhere like that.

---

### Post by glennric on 2008-02-28
You can find the version in numerous ways besides opening synaptic.  The terminal is always faster.  Type
```
apt-cache policy pkgname
```
to get the version number and a little more info.
```
apt-cache show pkgname
```
gives even more info.  Those work for any package in your activated repositories, whether they are installed or not.
If the package is installed you can type
```
dpkg -l pkgname
```
to the get version and a short description.

---

