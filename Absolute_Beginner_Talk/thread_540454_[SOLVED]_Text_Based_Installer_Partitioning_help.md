---
title: "[SOLVED] Text Based Installer Partitioning help"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by mramsey on 2007-09-01
OK, I am mid install with Feisty 7.04 using the alternate cd.  I am at the partitioning screen. I am uncertain which choice to select here. I have windows XP installed and want to split with 60GB to Ubuntu. Advise please.:confused:

---

### Post by Bachstelze on 2007-09-01
Is your Win XP partition taking the whole drive, right now ? If so, abort the installation and resize it using GParted. Then, restart the installation and choose "Use the largest continuous free space".

---

### Post by mramsey on 2007-09-01
> **HymnToLife said:**
> Is your Win XP partition taking the whole drive, right now ? If so, abort the installation and resize it using GParted. Then, restart the installation and choose "Use the largest continuous free space".

Not sure if I follow you.. the windows install is a standard install so I assume C:/ partition. I have never used g parted please elaborate.

---

### Post by Bachstelze on 2007-09-01
[http://gparted.sf.net](http://gparted.sf.net)

Download the GParted Live CD ISO and burn it. Then, boot from it and use it to resize your Windows partition.

---

### Post by bone2006 on 2007-09-01
When you reboot with gparted liveCD make sure you create a swap. Then you'll have 3 partitions
NTFS, EXT3 and your Swap (make swap 2 or 3 times the size of your ram).  
When you stick the alternative CD back in select the manual partition open, then make sure you click edit and change the new EXT3 to "/'" meaning you want root to install there and then click next.

---

### Post by Bachstelze on 2007-09-01
No need to create the partitions now, they can be created during installation.

---

### Post by mramsey on 2007-09-01
> No need to create the partitions now, they can be created during installation.

Ok its installing now...We shall see! I will post my results.:)

Edit:
Alas all finished. Everything seems to be in order. No issues so far!

---

