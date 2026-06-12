---
title: "Can Ubuntu Share Panther partition like OS9 does?"
date: 2007-03-11
forum: Apple PPC Users
---

### Post by jimwg on 2007-03-11
Greetings All!

The subject lines tells it all. I just took a tour of the install CD I burned and Ubuntu looks fascinating. Hang up is my iBook already has a Tiger and a Panther partition each, with OS9 sharing the Panther one. I'd scrub the Panther side but only if I REALLY have to in order to install Ubuntu on my HD. Question; is there any way for Ubuntu to share a partition with another OS like OS9 does with Panther?

Thanks for any assist!

James Greenidge
:confused:

---

### Post by Paerez on 2007-03-11
You can use a virtualization program to run linux inside osx, much like os9 runs inside osx. Parallels is one, but it costs money.

VMWare is free, but its just for linux and windows. I don't know if there are any free mac ones.

---

### Post by calum on 2007-03-11
> **Paerez said:**
> You can use a virtualization program to run linux inside osx, much like os9 runs inside osx. Parallels is one, but it costs money.

VMWare is free, but its just for linux and windows. I don't know if there are any free mac ones.

Parallels and VMWare are for x86, this is the PPC forum :)

On PPC, you might investigate Mac-on-Linux, which allows you to run OS X in a window on your Linux desktop.

---

### Post by grazie on 2007-03-11
You can share for both reading and writing HFS partitions, but not HFS+ partitions. If you attempted to write to an HFS+ partition from linux you will get a disaster. HFS+ can easily be made HFS by turning off journaling from OS9/OSX. 

Also by adding a driver to OSX, Ext2 partitions can also be shared, but there are limitations. For further info read [here]("http://forums.macrumors.com/showthread.php?t=88563") and elsewhere.

---

