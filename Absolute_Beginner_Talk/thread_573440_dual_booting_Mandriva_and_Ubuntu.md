---
title: "dual booting Mandriva and Ubuntu"
date: 2007-10-11
forum: Absolute Beginner Talk
---

### Post by Benbow on 2007-10-11
I would like to install Mandriva on to my hard drive which has Ubuntu on it which I use extensively. (no windows!). I have the Mandriva live cd which performs ok and would prefer to install from this - I know that I can do this but I must keep my Ubuntu totally intact as it is my working system.
Could anyone talk me through this, please?

---

### Post by floke on 2007-10-11
Backup important data. Create a new partition for Mandriva (you may have to make a /home partition too - I'm not sure if Mandriva forces this, but PCLOS (based on Man,,,) does.

Then I guess you install!

One thing you might want to do is select the option for installing grub into the root partition rather than the mbr so that your ubuntu /boot/grub/menu.lst remains in control of it.

---

### Post by Shazaam on 2007-10-11
Which version of Mandriva? All of my experiences have been with One 2007.1
My suggestion to you is to download and slowly burn a gparted livecd first

[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

and use it to shrink Ubuntu if you need to, make an EXTENDED partition to hold Mandriva, and install it to the EXTENDED partition.
Mandriva (the one I used) hid the partitions that held Ubuntu and Mepis (marked the WHOLE drive as "unallocated") and made three partitions (/boot, /root, and /home) no matter if I tried manual partitioning or not. Needless to say I lost the other os's. So be carefull.

---

