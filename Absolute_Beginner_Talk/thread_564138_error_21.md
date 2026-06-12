---
title: "error 21"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by carusoswi on 2007-09-30
Ok, installing 7.04 on a computer with three drives.  XP is on C, I'm installing to the second slave.  It is a 160 GB drive.  Install goes ok.  Restart returns GRUB loading stage1.5, GRUB loading, please wait..., then Error 21.

What's that and how would I fix it.  Tried reinstalling, same result.

Thanks for any help.

Caruso

---

### Post by Pumalite on 2007-09-30
[http://users.bigpond.net.au/hermanzone/p15.htm#21](http://users.bigpond.net.au/hermanzone/p15.htm#21)

---

### Post by Jimmyfj on 2007-09-30
Grub error 21 means: "Cannot find disk" - You need to check the boot sequence in your system BIOS. Read more about the error:

[http://www.linuxquestions.org/questions/showthread.php?threadid=338856](http://www.linuxquestions.org/questions/showthread.php?threadid=338856)

---

### Post by carusoswi on 2007-10-01
Ok, I read through all the links.  I guess I need to use my XP disc to restore the MBR for XP, then delete Menu1.st and try the install again.
My remaining question would be why did this happen?  I followed the instructions for installing Ubuntu.

Caruso

---

### Post by alienexplorers on 2007-10-01
Try getting and using the Super Grub Disk to repair the MBR and to reload Grub.

---

