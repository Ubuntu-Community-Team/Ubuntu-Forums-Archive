---
title: "Formating NTFS and reinstalling XP, effects on Ubuntu"
date: 2005-11-07
forum: Absolute Beginner Talk
---

### Post by redstorm on 2005-11-07
Hi everyone, I migrated to ubuntu about two months ago and I've been quite happy with it. Still at office there are some applications where I still require the use of XP. I created a NTFS partition so I can have both systems on the hard drive and its been working fine.

My XP instalation has become buggy the last few days and I have confirmed it was the cause of some options I should have set when Installing. I now want to clean up my NTFS partition and reinstall XP freshly again but I wonder if this will have a secondary effect on my ubuntu instalation.

I am using GRUB to load the OS of my choice when the computer starts. I followed the suggested instructions when I initially created the partitions and first created NTFS and then Linux. I just wonder if formating and reinstalling XP on my NTFS will rewrite the MBR of my HardDrive and lock me out of Grub, making my Ubuntu system unaccesible.

I appreciate any help anyone can give me.

BTW, my hard drive is SATA and it is setup as RAID.

Thanx.

Jose R. Lopez

---

### Post by tonysathre on 2005-11-07
reinstalling XP will replace your MBR, but dont worry it wont hurt anything, after installing XP just put in the ubuntu install CD and reinstall grub

---

### Post by 23meg on 2005-11-07
That's exactly what it will do. [This thread]("http://www.ubuntuforums.org/showthread.php?t=56668") should help you.

---

### Post by redstorm on 2005-11-07
excellent, I appreciate the replies.

I will try this shortly and will post here the results.  Hope they are succesfull :P.

Jose

---

### Post by manicka on 2005-11-07
This may also be of some help

[http://doc.gwos.org/index.php/Restore_Grub](http://doc.gwos.org/index.php/Restore_Grub)

---

