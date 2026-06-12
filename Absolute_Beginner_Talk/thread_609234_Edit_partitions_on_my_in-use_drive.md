---
title: "Edit partitions on my in-use drive?"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by rollerdiscoman on 2007-11-10
Can I, by chance, edit the partitions of the drive I am running my Linux on? I want to install Xubuntu on my Ubuntu-running drive, but with minimal space.

Thank you.

---

### Post by gn2 on 2007-11-10
> **rollerdiscoman said:**
> Can I, by chance, edit the partitions of the drive I am running my Linux on? I want to install Xubuntu on my Ubuntu-running drive, but with minimal space.

Thank you.

No need to alter any partitions, run this in a terminal: sudo apt-get install xubuntu-desktop

You can then log out by pressing Ctrl+Alt+Backspace, click Sessions and select XFCE and log-in again, you will be running Xubuntu.

You will also be able to choose whether to have Gnome (Ubuntu) or XFCE (Xubuntu) set as default.

---

### Post by scmason on 2007-11-10
Even IF a partitioning tool will let you do this, it would be a very bad idea as the behavior is likely undefined.  Certainly, fdisk will allow you to edit the partition table of a mounted drive, but this isn't the right way to do it.

Load a boot disk or live CD and do it from there. If you just want to play with or test another distro, why not try out one of the many virtual machines out there? 

[/Kernel based Virtual Machine]("http://en.wikipedia.org/wiki/Kernel-based_Virtual_Machine"),  [XEN]("http://en.wikipedia.org/wiki/Xen") or [VMWare]("http://en.wikipedia.org/wiki/Vmware") are good solutions.

---

