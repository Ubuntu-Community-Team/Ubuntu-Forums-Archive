---
title: "Cannot boot XP"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by animere on 2008-04-05
Hey Guys. Long time user first time with a problem.

I have been using Ubuntu for a while now ~8mos. I recently upgraded to a larger hard drive and have Ubuntu, Vista and XP installed (I work for an ITS so I need to play around on multiple systems). I have Vista and Ubuntu working but I cannot boot from my XP partition and I do not have an XP cd on me to try and recover the install. 

My problem is whenever I get to grub and try to boot XP it says, "Now Loading..." and stops.



[QUOTE=Grub/menu.lst]title     Windows Xp Media Center Edition
rootnoverify     (hd0,3)
savedefault
makeactive
chainloader     +1[/QUOTE]


[QUOTE=fdisk -l]Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009b098

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3187    25599546    7  HPFS/NTFS
/dev/sda2            3188        4207     8193150   83  Linux
/dev/sda3            4208        4462     2048287+  82  Linux swap / Solaris
/dev/sda4   *        4463       30401   208355017+   7  HPFS/NTFS[/QUOTE]


Any help would be appreciated

---

### Post by Inxsible on 2008-04-05
The entries look alright, provided the XP was in the 4th partition. Maybe you should try a chkdsk on the partition. Unfortunately you will need a XP cd for it. Maybe borrow from a friend or get it thru other means ?

---

### Post by bumanie on 2008-04-05
You could look at trying to boot you system with easybcd bootlaoder. There are tutorials/web pages about triple booting. you can get easbcd here and there are some guides on the site too. [http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)
Grub page may help, but I can't remember reading about triple booting, but it is the definitive site on grub. [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by animere on 2008-04-05
Yeah I'm gonna try this iso for XP [http://www.mybittorrent.com/info/674925/](http://www.mybittorrent.com/info/674925/) and then I'll try the other boot loader. I'll keep you all updated

---

### Post by lswest on 2008-04-05
also, you can try adding ```
map (hd0) (hd1)
map (hd1) (hd0)
``` after the root line, it fixed it for my computer.  However, my computer had 2 hard drives, yours doesn't.  Give it a shot anyways.

---

### Post by animere on 2008-04-05
> **lswest said:**
> also, you can try adding ```
map (hd0) (hd1)
map (hd1) (hd0)
``` after the root line, it fixed it for my computer.  However, my computer had 2 hard drives, yours doesn't.  Give it a shot anyways.

I tried the above and I get

> Now Loading...
A disk read error occured
Press ctrl + alt + del to restart

---

### Post by animere on 2008-04-06
Tried the following to no avail:

> sfdisk -d /dev/sda | sfdisk --force -no-reread -H255 /dev/sda
hexedit /dev/hda1 (/dev/sda1 was my windows partition)
[press enter]
7e1a
FF
ctrl-x, "y"


---

### Post by animere on 2008-04-06
I wonder if this has anything to do with this. My drive containing XP is not the size of the partition its in

[IMG]http://www.computerforum.com/attachments/computer-memory-hard-drives/2446d1207527455-dive-not-matching-partition-size-untitled.jpg[/IMG]

BUT gParted says:

[IMG]http://www.computerforum.com/attachments/computer-memory-hard-drives/2447d1207534989-dive-not-matching-partition-size-screenshot.jpg[/IMG]

---

