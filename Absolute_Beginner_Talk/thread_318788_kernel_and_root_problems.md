---
title: "kernel and root problems"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by kiwibanaan on 2006-12-14
I just started out with ubuntu, but I don't know how I can get root acces.
simple question I think:) 

and another one
where can I find my kernel? I read a thousand times it should be under /usr/src/
But when I open the directory there is nothing there.

I need it to install my VPN Client, and finally get internet connection and drop windows.

Thanks!

---

### Post by useResa on 2006-12-14
> **kiwibanaan said:**
> I just started out with ubuntu, but I don't know how I can get root acces.
simple question I think:) 
Thanks!
More information on root access can be found [here](https://help.ubuntu.com/community/RootSudo)

Maybe someone else can help you out with your kernel question.

---

### Post by mr_samsonov on 2006-12-14
Hi there, 

I think your kernel is in /boot/

Also you can get root access using 

sudo -s

Or just 

sudo <command>

---

### Post by kiwibanaan on 2006-12-14
I'll try it out right away

OFFTOPIC:

you guys react FAST:o :D

---

### Post by dwblas on 2006-12-14
You don't have the source for the kernel on Ubuntu by default, so it isn't in /usr/src/linux.  It will be there for systems that compile their own kernel, like Gentoo.  All you download in Ubuntu is the already compiled version, not the source.  Check out linux and linux-doc in synaptic, or you can download a vanilla kernel from kernel.org.  Keep A Backup Of Your Original Kernel that is in /boot in case you compile over it from some reason.  Also, add an entry to grub for the new kernel, do not replace the entry for your existing kernel, so you can boot to the old kernel when the new one doesn't work.  If this is your first attempt at compiling a kernel, get as much help as you can on what to configure.

---

### Post by sailor2001 on 2006-12-14
> **dwblas said:**
> You don't have the source for the kernel on Ubuntu by default, so it isn't in /usr/src/linux.  It will be there for systems that compile their own kernel, like Gentoo.  All you download in Ubuntu is the already compiled version, not the source.  Check out linux and linux-doc in synaptic, or you can download a vanilla kernel from kernel.org.  Keep A Backup Of Your Original Kernel that is in /boot in case you compile over it from some reason.  Also, add an entry to grub for the new kernel, do not replace the entry for your existing kernel, so you can boot to the old kernel when the new one doesn't work.  If this is your first attempt at compiling a kernel, get as much help as you can on what to configure.

synaptics has your kernel  "linux-image" 2.6.17-19-386  is the latest

---

