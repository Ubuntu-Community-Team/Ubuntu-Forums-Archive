---
title: "&gt; Need advice on deleting partition"
date: 2011-06-23
forum: Any Other OS
---

### Post by Ba6 on 2011-06-23
I'm currently in the process of dual-boot installing BT5 *oh joy!*

I'm running an hp mini 110, by default she comes with 4 partitions already created, so I need to delete one to create the partition for BT5

The current partitions are as follows;
SYSTEM: 200mb
C: (Windoze 7) 100gb --I've shrunk it to allow space for the BT5 install
D: RECOVERY (Windoze 7 backup) : 16gb
*:HP_TOOLS : 103MB

I'm trying to figure out which I should knock out

I've narrowed it down to SYSTEM or HP TOOLS however, I'm not exactly sure which
does what [ iRn00b =( ]

Which one, if any, can I safely delete?
If I'm unable to delete any, is there a workaround?

---

### Post by Elfy on 2011-06-23
Thread moved to Other OS/Distro Talk.

---

### Post by skatinjj on 2011-06-23
Why not just install it onto a USB flash drive or other external drive.

As a HP technician, I wouldn't recommend deleting either of those partitions.

---

### Post by Ba6 on 2011-06-23
Thanks, I guess I'll have to do that, its probably for the best anyways.

So does this mean dual-booting on her isn't possible, without damaging other parts?

---

### Post by wolfen69 on 2011-06-23
...................

---

### Post by skatinjj on 2011-07-13
> **Ba6 said:**
> Thanks, I guess I'll have to do that, its probably for the best anyways.

So does this mean dual-booting on her isn't possible, without damaging other parts?

I'd suggest wubi install from within windows.

---

### Post by oldfred on 2011-07-13
The 103MB is not much to backup. And once you have made teh recovery DVDs and a repair CD you can delete both partitions. 

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Besure to create recovery DVD(s) first.
HP tools partition discussion:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
Shrinking a Windows 7 partition is best done in Windows. 
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)
The Hedge show graphically how to delete & create partitions:
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)

Make your own Windows recoveryCD/repair:
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.

Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

---

### Post by mips on 2011-07-13
> **skatinjj said:**
> 
As a HP technician, I wouldn't recommend deleting either of those partitions.

They are not required, I wipe them whenever I come across them.

What is your reasoning for not wiping them?

---

