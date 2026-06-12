---
title: "Lost boot table?"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by kinfe on 2007-05-09
Tried installing Ubuntu Ver. 6 and got stuck at step 5/6 of hard disk partitioning; tried it for three times, each time I back out and re-install and always have to back out.  Now, I can't get my Vista to boot, I get a ' - ' blinking after the BIOS.  I su to root and manage to get the info below, can someone help me restore my Vista or boot table?

Disk /dev/sda: 120.0 GB
255 heads, 63 Sectors/tracks, 14593 Cylinders
Unit.........

Device         Boot   Start    End     Blocks        Id    System

/dev/sda1                1        6       48163+      de   Dell Utility
/dev/sda2      *        7        9015  72364792    7    hpfs/ntfs

---

### Post by Foxmike on 2007-05-09
I am not an expert but it seems the MBR (Main Boot Record) is not right.  That is what tells the computer to do to boot.  I would suggest to try install Vista again but I might be wrong.  Maybe the Ubuntu CD you have is corrupt.  Did you check the CD before the installation?  You can do it with the menus you see when you restart the computer before to load Ubuntu.

---

### Post by kinfe on 2007-05-09
Thanks for  help.  I just re-installed vista (need the box up early in the morning).  CD is ok, but when it gets to partitioning (resizing) it then seems to hang in a loop.  I'll try again when I have a free box.  Now, there are lots of backup/restoring to do before sun rise.

Thank again.

---

### Post by zvacet on 2007-05-10
[http://ubuntuforums.org/showthread.php?t=371530&highlight=vista]("http://ubuntuforums.org/showthread.php?t=371530&highlight=vista")

---

