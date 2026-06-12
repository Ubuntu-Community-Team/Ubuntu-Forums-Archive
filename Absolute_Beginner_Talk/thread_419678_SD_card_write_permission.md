---
title: "SD card write permission"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by Tangerined on 2007-04-23
Hi i got my sd card mounted but I can't write to it because its read only. I found this entry in my mtab file 
/dev/sde1 /media/MICROSD vfat ro,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077 0 0
do i need to change something in that line for me to be able to write as well or something else?

---

### Post by finer recliner on 2007-04-23
excerpt from my mtab:
/dev/mmcblk0p1 /media/SDcard vfat rw,utf8,umask=007,gid=46 0 0


^line for my SD card mounted to /media/SDcard. i have rw access.


heres the line from fstab too:
/dev/mmcblk0p1 /media/SDcard vfat rw,utf8,umask=007,gid=46 0 0

---

### Post by Tangerined on 2007-04-23
ok, i wrote this into my fstab
/dev/sde /media/MICROSD vfat rw,utf8,umask=007,gid=46 0 0

but when i tried to mount i got the message:
 
mount: block device /dev/sde is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sde,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by finer recliner on 2007-04-23
write protected....maybe you have the physical write lock on (little switch on the side of the card)

if not, then maybe your SD card isnt vfat (ntfs? something else?)

---

### Post by silverglade00 on 2007-04-23
That little write protect switch on my SD card had me ripping out my hair for a week. Never knew it was there. It gave me the same problems that Tangerined has. Wish I had seen this thread back then. :)

---

### Post by Tangerined on 2007-04-23
Ok I checked the lock tab on the sd card and its not in lock position. Also the sd card is in fat16 format. :(

---

