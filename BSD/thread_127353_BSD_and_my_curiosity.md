---
title: "BSD and my curiosity"
date: 2006-02-08
forum: BSD
---

### Post by qalimas on 2006-02-08
Ok, so I've never used a BSD before, and I was reading some topics here and peopel are saying how wonderful it is, how fast it is, etc... what's great about it?  Is it really that much faster?  Can I run all my Linux programs on it (KDE, Quanta, Kopete, etc etc, Wesnoth)?  I'm downloading a prebuilt FreeBSD virtual Machine for VMPlayer and am going to try it, what should I expect?

---

### Post by xequence on 2006-02-08
BSD aparently runs considerably faster...

I think FreeBSD comes with Gnome and KDE. It also has a (working) linux compatability layer so you can run linux programs on FreeBSD.

---

### Post by fuscia on 2006-02-08
[QUOTE=qalimas]I'm downloading a prebuilt FreeBSD virtual Machine for VMPlayer and am going to try it, what should I expect?[/QUOTE]

what's this all about? 

i'm trying to get a working live version of netbsd. i couldn't get 'newbie' to boot. apparently, there's a new update of it where some boot problem has been taken care of. [http://arudius.sourceforge.net/](http://arudius.sourceforge.net/)

---

### Post by qalimas on 2006-02-08
[http://www.vmware.com/products/player/](http://www.vmware.com/products/player/)
[http://www.vmware.com/vmtn/vm/community.html](http://www.vmware.com/vmtn/vm/community.html)

Turns out the VM was stripped, so I'm going to have to get Qemu and make a vmdk file for hte harddrive and install from ISOs.  I'm going to try it tomorrow, I just want to see how it runs and how easy it is to get my programs on and updated, if it's as easy but better than Linux, I'll head for it, but I'm unsure, so I'll be testing it for a couple months before I move over :P

---

### Post by JAwuku on 2006-02-09
I've also just installed FreeBSD 6.0 in Kubuntu, under Parallels Workstation. It seems to install fine, and run at good speed. Unless you have the DVD, you have to install things like KDE yourself. However, FreeBSD has a good packaging system, which can automatically fetch source from the net, configure, and compile it, as well as automatically fetching any dependencies if needed. Quite neat! KDE is compiling as I write this.

Of course, you can just install binary packages instead, if you don't feel masochistic:D 

The only drawback is that there is no 3D support for ATI cards. I'm not sure what the situation is for Nvidia.

---

### Post by Stormy Eyes on 2006-02-09
[QUOTE=JAwuku]
The only drawback is that there is no 3D support for ATI cards. I'm not sure what the situation is for Nvidia.[/QUOTE]

nVidia has a driver for FreeBSD [here](http://www.nvidia.com/object/freebsd_1.0-8178.html).

---

### Post by drucer on 2006-02-10
FreeBSD does not have any sophisticated audio system like Linux ALSA and Jack. This means you can't run Linux pro-audio apps (Jack, Ardour, Rosegarden.. etc.) on it. Not even with Linux compatibility layer.

---

