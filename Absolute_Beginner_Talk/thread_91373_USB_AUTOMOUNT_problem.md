---
title: "USB AUTOMOUNT problem"
date: 2005-11-17
forum: Absolute Beginner Talk
---

### Post by Sampo on 2005-11-17
Konqueror gives the sda empty file error when I stick in my USB Flashdisk. It seems that this is is a common problem for 5.10 breezy. I have however, not been able to find understandable help or solution for the problem.

---

### Post by bulldogzerofive on 2005-11-17
I got this from another thread  (forget which one) and have it in my notes, so i can't take credit for the solution... but i don't know who did it.

add hal to the user groups cdrom and plugdev

if they are not installed already, use synaptic to install: devfsd, liblockfile1, lockfile-progs, usbmount, usbview

then reboot.

You can also try to run: sudo restart hotplug

good luck

--Seppo

---

### Post by patrick295767 on 2005-11-19
I got same troubles: 
the way i am doing to solve this is to start a script in rc2.d
[http://www.ubuntuforums.org/showthread.php?t=64557&page=7](http://www.ubuntuforums.org/showthread.php?t=64557&page=7)

---

