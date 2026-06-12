---
title: "EeePc 1015PN, win/ubuntu dual boot, Partitions"
date: 2011-07-09
forum: Asus Ubuntu Support (CLOSED)
---

### Post by seppel1 on 2011-07-09
Hello,

i just got an EeePc 1015PN. I plan to install Ubuntu  alongside Windows 7. The problem is that their are already 4 primary  partitions:

 /dev/sda1: ntfs, 100 GB, used for Windows
 /dev/sda2: fat32, 15 GB, hidden, i'm not sure, i think it's the recovery partition and/or Express Gate
 /dev/sda3: ntfs, 183 GB
 /dev/sda4: unknown, 16 MB, again i'm not sure, maybe used for boot booster

I want to have 50 GB for Win, 50 GB for Ubuntu (/ and /home), keep the recovery partition and a huge partition for data.

Now I'm wondering which way is the best for achieving this.

#1:  scale /dev/sda1 to 50GB, move /dev/sda2, deleting /dev/sda3 and replace  it with an extended partition which is split into /, /home and data.
Problem:  when i move /dev/sda2 (using gparted) i get a warning message telling  me that moving a partition with bootsector might make my system unable  to boot.
i think moving this partition might damage the ability to recover.

#2: save a copy of /dev/sda2 to another drive and delete it ...

does anyone know how this can be done? 

#3:  delete /dev/sda4, scale /dev/sda1 to 50GB, use the space between  windows and recover for another extended partition split into / and  /home.
Problem: i think i will lose the boot booster option. 


So  my questions are: am i right about the use of partitions /dev/sda2 and  /dev/sda4? which way would be the best/safest way to partition the  drive?

---

### Post by bennyroger on 2011-07-09
I have the same netbook as you, I found out the best way was to remove sda3 and 4 and use that space for Ubuntu.
Bootbooster was gone as a choice in the bios, but its not a big loss....

---

