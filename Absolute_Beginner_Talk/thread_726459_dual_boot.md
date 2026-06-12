---
title: "dual boot"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by wobbiebobbie on 2008-03-16
hey guys could some body please direct me to a thread on how to do a dual boot when I allready have ubuntu 7.10 on my computer now I need to put WINDOZE on my computer my kids dont know how to use ubuntu. I will teach them to use ubuntu but for now they have to go back (not me ) thanks (PS I tryed it but lost my MBR on ubuntu )

---

### Post by FunkyJack on 2008-03-16
This might help

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by Tilex on 2008-03-16
Hi,
I'm afraid you can't dual boot with Windows AFTER you have installed Ubuntu.  Windows simply wants to be the only one on the computer it seems...

Maybe I'm wrong, but I've tried many times in the past, and it just didn't work.  I suggest you backup important data on a partition that won't get wiped out upon the installation of Windows.  Then, install Windows and Ubuntu afterwards.  This way, it should work fine because Ubuntu will "see" Windows installed and will ask you if you want to dual boot with Windows.

Good luck!

---

### Post by jan quark on 2008-03-16
check out this guides:

[http://apcmag.com/node/5162/](http://apcmag.com/node/5162/)

---

### Post by FunkyJack on 2008-03-16
> **Tilex said:**
> Hi,
I'm afraid you can't dual boot with Windows AFTER you have installed Ubuntu.  Windows simply wants to be the only one on the computer it seems...

Maybe I'm wrong, but I've tried many times in the past, and it just didn't work.  I suggest you backup important data on a partition that won't get wiped out upon the installation of Windows.  Then, install Windows and Ubuntu afterwards.  This way, it should work fine because Ubuntu will "see" Windows installed and will ask you if you want to dual boot with Windows.

Good luck!

Windows has only changed his MBR (Master Boot Record).
Grub will fix that very easy ;)

---

### Post by bumanie on 2008-03-16
It is far easier to install windows first. It is not impossible to do it the way you wish, but you will probably run into problems and would almost certainly have to restore grub and probably edit your /boot/grub/menu.lst and trick windows into thinking it on the first partition of the hard drive. If you don't have much on windows or ubuntu (sounds as though this is a fairly new setup), I'd reinstall again - windows first.
You can read this guide if you wish to install windows after ubuntu
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

