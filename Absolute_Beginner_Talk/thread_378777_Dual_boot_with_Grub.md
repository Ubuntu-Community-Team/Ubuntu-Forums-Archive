---
title: "Dual boot with Grub"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by orrinjelo on 2007-03-07
I got a little problem-chen.
I originally had Windows 2000 Pro installed on my laptop, then decided I wanted to try a dual boot Xubuntu/Win2000Pro.  So, I popped in the Live CD, installed.
I got my HD portioned; 2/3 of the drive for windows (hda1), 1/3 for xubuntu (hda2), then 260M for swap.  
So, first question--where do I put the "boot" flag?  I have it currently on hda2.
After this, it has the mount menu.  Second question--What goes where?  Swap obviously goes with swap, and I read that the Xubuntu partition goes to "/", but what about the Windows partition?  
So it goes through this, partitions, formats, whatever.  The final window lists the details, allowing me to select where I have Grub installed.  Question three--where do I put GRUB?  The default option is (hd0).
Yet, I've tried to keep everything at a default setting, and try to boot--Grub seems to start, but then crashes with Error 17.

Mind checking my settings and offering whatever advice?
Thx.
-OJ

---

### Post by mikewhatever on 2007-03-07
The Windows partition can be mounted in /media/hda1. Grub does go to hd0, so I looked up the error 17 here   [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
> 17 : Cannot mount selected partition
    This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB. 

Most commonly this is caused by using the 'root' command instead of 'rootnoverify' when booting Windows having the NTFS file system.
Edit your commands in your menu.lst or grub.conf file with 'rootnoverify' to get rid of this error message.

If you get this error when trying to boot Linux, check your grub conf. or menu.lst file and make sure to check your operating system entry's 'root (hdx,y)' details are correct.

You will need Super Grub Disk to boot Linux for you so that you can easily check and repair your operating system's entry in menu.lst.
Super Grub can boot your operating system by symlinks to the kernel if you use, from the Main Menu,--> Boot Gnu/Linux and  Other OSes --> Boot Gnu/Linux -->...

If you have used hard disk partitioning software recently and you have copied and pasted your partition that contains Grub, it probably has a different partition number now than it had before. You can use Super Grub Disk to re-install Grub. You will also need to edit /etc/fstab if your partition numbers have changed.



[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

