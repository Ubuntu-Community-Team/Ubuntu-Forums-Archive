---
title: "Really new to this and it wont install"
date: 2006-12-07
forum: Absolute Beginner Talk
---

### Post by GALAXY on 2006-12-07
I have CD of V6.06.1 LTS and I can install it as Live CD and try out the program (all runs well) I have since installed it and all seems to be ok, but when it reaches the end of the install process it asks for the CD to be removed and reboots. At which time it errors out looking for a Windows file. 
Im confused because I have installed it on a 10 Gb drive which has no other OS on it. I dont want it to be dual boot as I use removable caddies for different OS's.

---

### Post by wpshooter on 2006-12-07
Sounds like to me that maybe there are some remanents of M/S O/S still on the system.  But this seems sort of strange !!!

Get the **KILLDISK** program from this site and **WIPE** the drive completely clean and then reinstall Ubuntu.

[http://www.killdisk.com/](http://www.killdisk.com/)

Make sure you check the integrity of your Ubuntu CD by running the verification check found on the initial Ubuntu boot screen menu.

Good luck.

---

### Post by GALAXY on 2006-12-07
Thanx for the reply, Unfortunately I dont have the means to dload killdisk so unless I can get unbubtu up and running Im stumped. I have done a complete format of the drive but it still looks for windows.

---

### Post by pmasiar on 2006-12-07
Is it possible that your BIOS disables somehow writing to MBR (master boot record) on first disk? Sometimes it is set up as protection from viruses.

If changing BIOS options will not help, you can also try creating bootable floppy and use it to boot into your Linux disk. You will need to learn GRUB, but it is not that hard. You just learn GRUB sooner than other people. :-) There are couple of LiveCD distros specialized in recovery tools, like SystemRescue LiveCD.

---

### Post by GALAXY on 2006-12-07
Thanx guys Im giving it a go

---

