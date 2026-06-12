---
title: "changing kernel from generic to i386"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by grossespinne on 2007-06-26
Hi everybody!
I wanted to install Ubuntu 7.04 with the i386 kernel and therefore I downloaded [http://cdimages.ubuntu.com/releases/7.04/release/ubuntu-7.04-dvd-i386.iso](http://cdimages.ubuntu.com/releases/7.04/release/ubuntu-7.04-dvd-i386.iso)    
After installing it, however, I noticed that the installed kernel version was 'generic' and not 'i386'.

My question is:
is it possible to change the kernel from generic to i386 without having to reinstall the whole system and how do I  do that? If it is not possible then how do I reinstall the system so that it uses i386 kernel and not the generic one? (the default installation procedure did not give any choices about the kernel version)

TIA

---

### Post by Happy_Man on 2007-06-26
The generic is i386.

---

### Post by az on 2007-06-26
Not only is the generic kernel i386, but the optimisations are run-time.  You used to have to make those optimisations at compile-time (which is why there were different kernels like 686, k7, etc...)

What problems are you having?

---

### Post by grossespinne on 2007-06-27
I wanted to get my USB wireless card to work (see [http://ubuntuforums.org/showthread.php?t=483439](http://ubuntuforums.org/showthread.php?t=483439)) and in another forum I was suggested that I should use i386 kernel instead of the generic one.

---

### Post by aeiah on 2007-06-27
which howto are you following? because i just ignored the 'install the i386 kernel' bit on one howto and my card worked. it shouldnt be necessary since the generic one is basically the i386 with added bits where apt.

---

### Post by grossespinne on 2007-06-27
I followed the install instructions of ndiswrapper, there was no talk about i386 in those instructions.
But when I type modprobe ndiswrapper the system freezes and someone told me to try and change the generic kernel to i386 or i686.

---

