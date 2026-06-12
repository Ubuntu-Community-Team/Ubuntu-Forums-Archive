---
title: "Won't boot; 1st ubuntu install w/grub partitio"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by regbsn on 2008-03-31
XP Home in 1st 7.3 Gb partition. 12.7 Gb freespace. Tried to install Ubuntu 7.10 as follows:
*during partitioning:
**<logical>  for 9.0 Gb ext3 "/home" sdc5
**<logical>  for 2.54 Gb ext3 "/" sdc6
**<logical>  for 98.7 Mb ext3 sdc7
**<logical>  for 1.0 Gb swap sdc8

when asked if I wanted to install grub in MBR, I chose <no>
then chose /dev/sdc7 and chose continue.

Now I cannot boot beyond "Toshiba" splash page.
All I get is:
"_"

I used Alternate CD Install. (I have the live and Gparted live CDs also)

Please help!

---

### Post by Inxsible on 2008-03-31
i will post this to the unanswered posts team. Someone outta help you out soon !

---

### Post by regbsn on 2008-04-01
Used Alternate disk as rescue disc. Used "Re-install Grub" option and placed it into MBR. Now it works...
I get the usual GRUB menu and have so far booted into Ubuntu w/o apparent problems. Windows XP loaded without problems.

I wanted to have a separate /GRUB partition so that if a virus took out XP, then I could re-install XP without messing everything up. Now I will have to try to see what to do with the /dev/sda7 with the GRUB file already on it, when I get the nerve up...:)

I hope this fixes things...to be continued...?

Thanks

---

