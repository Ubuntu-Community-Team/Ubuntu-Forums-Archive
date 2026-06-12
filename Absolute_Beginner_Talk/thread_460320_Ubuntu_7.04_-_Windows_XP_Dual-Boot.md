---
title: "Ubuntu 7.04 - Windows XP Dual-Boot"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by mep916 on 2007-05-31
Hello Everyone,

Recently, I formatted and installed Feisty over a Windows Vista installation. Before the Ubuntu install, I was dual booting Vista and XP. Although GRUB worked perfectly, I had the Vista bootloader left over from the old Vista installation. 

I entered the Windows Recovery Console to fix the MBR and remove the Vista bootloader. Now Windows XP boots perfectly; however, I lost GRUB and cannot enter my Feisty installation.

Is there any way to recover GRUB without reinstalling Ubuntu.

ThanK You,
Michael

---

### Post by dstew on 2007-05-31
You can re-install grub from the Ubuntu LiveCD. Boot the live CD, open a terminal window, and enter **grub**. This will get you the grub command line prompt **grub>**. Then, enter```
find /boot/grub/menu.lst
```It should give you the output of the partition that the linux boot files are on, in grub-form, like (hd0,1). Use whatever output you get as grub's root in this command```
root (hd0,1)
```Then, install grub again into the MBR using```
setup (hd0)
```Next quit grub, remove the CD and reboot. Hopefully you will get the grub menu.

---

### Post by confused57 on 2007-05-31
You might have to use "sudo grub", I'm not sure:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by ronmarley1 on 2007-05-31
I've used the Super Grub Disk a few times and I think it's great.  Here's a link to a thread with links.
[http://ubuntuforums.org/showthread.php?t=419598](http://ubuntuforums.org/showthread.php?t=419598)

---

### Post by mep916 on 2007-06-02
Awesome! Using the Live CD, I entered into a terminal, typed the "setup (hd0)" code, and, Voila! GRUB is up and running - without any problems booting into WinXP.

Thanks again for the advice everyone!

-Michael

---

