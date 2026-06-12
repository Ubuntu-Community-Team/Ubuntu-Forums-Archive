---
title: "just installed, have a couple questions"
date: 2006-09-23
forum: Absolute Beginner Talk
---

### Post by faf112 on 2006-09-23
I got an old dual P3 Xeon workstation from my work.  I have XP on one hard drive and I just installed Ubuntu on another hard drive.  The installation was very easy.  At work I use RH and when I issue the top command I see two cpus, but when I do it on this machine I only see 1.  Do I have to set up ubuntu to see both my cpus?  XP sees both of them and it seems to be faster.  Second do I have to install emacs seperately or does it come with ubuntu?

Thanks

---

### Post by madmetal on 2006-09-23
open synaptic and search for emacs (i dont know if you need extra repos)
and then search for smp kernel..

---

### Post by ewl1217 on 2006-09-23
You need the 686-smp kernel instead of the default generic 386 kernel. Emacs does not come with Ubuntu and must be installed seperately. To take care of both issues at once, issue the following command at the terminal:
```
sudo apt-get update && sudo apt-get install linux-686-smp emacs21
```
You'll need to reboot to use the new kernel.

**EDIT:** I just realized that the package emacs is in the extra repositories, so you should install the package emacs21, which is in the main repositories, instead, since you probably haven't enabled any of the extra repositories.

---

### Post by faf112 on 2006-09-24
thanks for the help it is much faster now.  I see both processors in the system monitor but I still don't see it when I issue the top command.

---

