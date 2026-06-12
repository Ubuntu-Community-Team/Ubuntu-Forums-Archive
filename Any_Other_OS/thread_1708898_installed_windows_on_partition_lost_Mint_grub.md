---
title: "installed windows on partition lost Mint grub"
date: 2011-03-17
forum: Any Other OS
---

### Post by Kinetic1001101 on 2011-03-17
I have a singe 500 GB HDD in my tower. I have Windows XP on first  partition, Win7 on second partition, Unallocated third partition and  Mint on fourth partition. I am wondering when I enter the code:

sudo grub
> root (hd?,?)
> setup (hd?)

what do I put in place of the ? marks if I want to fix Grub loader?

I was thinking: 
> root (hd0,4)
> setup (hd0)

I am probably totally wrong.  Any help soon would be great. Am I even doing the write approach?

More  details:   I had four partitions before I installed Windows 7 (Part1..  XP , Part2 empy NTFS , Part3 unallocated and Part4 Linux Mint) Before  the Win7 install the computer would go into linux mint "grub" boot  loader and I would choose either Linux mint or XP.  Worked fine. Then I  lost that after installing Win7... No I have different boot screen  allowing only older version of windows(XP) or Win7.   What to do?

Thanks in advance!

JC

---

### Post by andrewthomas on 2011-03-17
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by oldfred on 2011-03-17
Does Mint use grub or  grub2. The way to reinstall is different.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Windows moves all the boot files from a second install to the first install. Windows only boots from the primary partition with the boot flag. So if XP was your first install & had boot flag, then win7's boot files are in the XP partition. Grub will not then find the win7 install to boot as the boot files are only in the XP partition. Since 7 is newer than XP, it may have converted the boot in the XP install to a win7 boot and added the XP boot to a win7 menu.

To get each MS to have its own boot loader make a second primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

---

### Post by Hippytaff on 2011-03-17
> **andrewthomas said:**
> [https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

Are you^ a link bot - keep seeing your link posts dotted around :-D

---

