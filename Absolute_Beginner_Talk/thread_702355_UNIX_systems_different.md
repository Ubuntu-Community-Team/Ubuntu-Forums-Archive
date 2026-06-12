---
title: "UNIX systems different?"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by KOTAPAKA on 2008-02-20
What are the major differences between different UNIX systems (FreeBSD, OpenBSD, NetBSD, Solaris,MINIX and of course Linux). Is software universal for all of them? I mean is software that runs under Linux going to run under Solaris for example or FreeBSD? I am asking because I have had this picture called "Unix history" and it is basically a time line showing the evolution of Unix systems starting from UNIX-PDP7 and I want to know what differences have evolved along with the OS's. 10x

---

### Post by justleen on 2008-02-20
No, the software is not universal. Not all software will run on both unix and linux.. most software is OS specific (tru64 apps will not run on hp-ux)  the major difference is how they handle their hardware, adress memory, file system structure etc.  
Some apps will compile on any OS, since all you need is a C+  compiler. still, i wouldnt wanna try to install a src package for ubuntu on a tru64 machine.. The OS'es are simply to different.. 
Plus, there is another mayour difference: hardware. most of our server are Alpha machines. when writing programs, you need take into account what kind of system it is going to run on. (Linux just happens to be ported to any processor know to man )
Linux is not unix. If you look at the unix history picture, there is a split between berkley Unix and  SysV unix.  Good old linus took a SysV based system as a prototype for the linux kernel. there are still some remants of that to be found (the SysV logging for example) on your linux current machine.
Besides, this goes for all the different Linux distro as well. Yes, in theory i can compile from source Ubuntu and on Gentoo, but this doenst mean it will actually do so without problems..

think of it this way, even though they all share the same ancestor, it doenst mean  all the offspring  know their family tree  :)  

in windows terms: try installing a Vista app on Win95...

---

### Post by ruy_lopez on 2008-02-20
[This]("http://upload.wikimedia.org/wikipedia/en/1/11/Unix-history.svg") flow-diagram shows the cross-propagation of different strains of Unix over time.

The underlying architecture and the system calls made available by the kernel are what determines whether software runs on different systems, and how straightforward it is to port.

---

