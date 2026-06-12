---
title: "BIG ERROR- Please Help!"
date: 2006-04-04
forum: Absolute Beginner Talk
---

### Post by dylonium on 2006-04-04
I installed the entire Ubuntu Linux OS, and it all seemed to work fine until it restarted an dI got an error reading:

Grub Loading stage 1.5.
Error 21

Now, I tried to reinstall, but it still wouldn't work. I also tried to run my Windows XP, but that wouldn't work either. I 50% partitianed my 250GB External HDD and installed Ubuntu on this HDD, although I have a 80GB internal HDD with my system files on it. Does the 250GB HDD being connected via USB affect this? How can I get my Windows back and working? Can I use the live version of Ubuntu to fix this all? Please reply FAST!

P.S. I'm on my moms computer!

---

### Post by catlett on 2006-04-04
If you want windows back and then trouble shoot after you feel comfortable, you can fix your windows boot record. Get your XP install disk or your recovery disks that came with your computer. Boot to the disk like you did with the Ubuntu install disk. Choose recovery mode. You want to get in recovery mode and get to a command line. Enter ```
fixmbr
``` this will reinstall your windows boot manager to the MBR (master boot record). It appears Grub (the boot loader that Ubuntu uses) did not install properly. There are ways to fix this but I don't know them. Since noone has posted I figured I'd at least tell you how to get your windows boot back.
If you want search for info on Grub. There are plenty of previous posts that deal with this.

---

### Post by sn123 on 2006-04-04
[QUOTE=dylonium]I installed the entire Ubuntu Linux OS, and it all seemed to work fine until it restarted an dI got an error reading:

Grub Loading stage 1.5.
Error 21

Now, I tried to reinstall, but it still wouldn't work. I also tried to run my Windows XP, but that wouldn't work either. I 50% partitianed my 250GB External HDD and installed Ubuntu on this HDD, although I have a 80GB internal HDD with my system files on it. Does the 250GB HDD being connected via USB affect this? How can I get my Windows back and working? Can I use the live version of Ubuntu to fix this all? Please reply FAST!

P.S. I'm on my moms computer![/QUOTE]
You can use Windows XP install CD to fix it, put the CD & make sure that in the BIOS you have CD Drive as the first boot option and follow the instructions on this page to start Recovery Console & using fixmbr
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true)

S

---

### Post by Kapre on 2006-04-04
[QUOTE=dylonium]I installed the entire Ubuntu Linux OS, and it all seemed to work fine until it restarted an dI got an error reading:

Grub Loading stage 1.5.
Error 21

Now, I tried to reinstall, but it still wouldn't work. I also tried to run my Windows XP, but that wouldn't work either. I 50% partitianed my 250GB External HDD and installed Ubuntu on this HDD, although I have a 80GB internal HDD with my system files on it. Does the 250GB HDD being connected via USB affect this? How can I get my Windows back and working? Can I use the live version of Ubuntu to fix this all? Please reply FAST!

P.S. I'm on my moms computer![/QUOTE]


Dylonium - from what you've stated above, it seems your XP is loaded on your 80Gig HD (not on the external - 250 Gig). If XP is loaded on your 80 gig, follow what Sn and Catlett stated below. If you still want to load Ubuntu on your external HD, look at this [thread]("http://www.ubuntuforums.org/showthread.php?t=80811&highlight=external+hd")

K

---

### Post by dylonium on 2006-04-05
Thanks for everything! Now i just have to find my windows boot disk!

---

