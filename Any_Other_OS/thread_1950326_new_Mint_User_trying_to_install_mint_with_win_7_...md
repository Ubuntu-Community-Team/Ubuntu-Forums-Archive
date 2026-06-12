---
title: "new Mint User trying to install mint with win 7 .. help pls ?"
date: 2012-03-31
forum: Any Other OS
---

### Post by newmintuser on 2012-03-31
hey everyone how are you doing ...

i just done downloading linux  mint 12 gnome dvd 32bit and done extracting it on my USB drive using    Universal USB Installer (UUI) ......

i have win 7 working on my pc .....

i  did reboot the pc trying to boot from the USB flash drive to install  mint on my  D , partition ..... once trying to start looding files from  the USB drive i get this line


SYSLINUX ... 3.86  2010-04-01 EBIOS copyright  (c) 1994-2010 H. Peter Anin et al .......  and then that's it

the screen stay like that untill i hit the reset button cuz nothing will work to reset the PC >> 

i did google it and find an old topic here on one of the pages here and got his ,,, but still nothing worked wth me
the topic by [JackNocturne]("http://ubuntuforums.org/member.php?u=1105556")

Use USB Creator, its the simplest.

After you have created the USB boot disk with it, modify the following in the disk.


Go to root of USB flash disk to the folder /syslinux and find the file syslinux.cfg

Edit the file with a text editor; under the line

Code:

ui gfxboot bootlogo

change to
Code:

gfxboot bootlogo

then save.

Reboot to test it now

.......................................................................................

there is no ui gfxboot bootlogo code at all in my  syslinux.cfg file ????? what to do now ?


now i am so sad cuz i was on my way to move from using Win 7 ot Mint ..... 

hope to get help ASAP ......

---

### Post by howefield on 2012-03-31
Thread moved to "*Other OS/Distro Talk*" forum.

---

