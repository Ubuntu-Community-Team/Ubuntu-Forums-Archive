---
title: "Mounting DVDrom and DVD RW/CDRW"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by bobpur on 2007-11-21
I have a little problem with a fresh Ubuntu v7.10 install with all updates that I need help with. This is a new one on me.
My DVDrom and CDrom is not detected on this machine. 

bobpur@Ubuntu-desktop:~$ dmesg | tail
[17271.646115] sr: ASC=0x6 <<vendor>> ASCQ=0xf4
[17273.649057] sr1: CDROM (ioctl) error, command: Test Unit Ready 00 00 00 00 00 00
[17273.649080] sr: Sense Key : Medium Error [current] 
[17273.649086] sr: ASC=0x6 <<vendor>> ASCQ=0xf4
[17275.651815] sr1: CDROM (ioctl) error, command: Test Unit Ready 00 00 00 00 00 00
[17275.651840] sr: Sense Key : Medium Error [current] 
[17275.651845] sr: ASC=0x6 <<vendor>> ASCQ=0xf4
[17277.654762] sr1: CDROM (ioctl) error, command: Test Unit Ready 00 00 00 00 00 00
[17277.654787] sr: Sense Key : Medium Error [current] 
[17277.654792] sr: ASC=0x6 <<vendor>> ASCQ=0xf4
bobpur@Ubuntu-desktop:~$ 

I, also, tried: mount /mnt/cdrom and mount /mnt/cdrom0 and mount /media/cdrom0 with other error messages.
I'll keep looking and check back here later.  Thanks.

---

### Post by polhen on 2007-11-23
hi everybody !

i have problem with mounting my dvd and cdrom on ubuntu 7.04
what should i do, to use this devices..?

any help greatly appreciated....

regards
pol

---

### Post by markharding557 on 2007-11-23
have a look in hardware information to see if its in there

---

