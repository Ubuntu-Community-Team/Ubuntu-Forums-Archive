---
title: "MP3 player not mounting"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by Niloc on 2007-12-04
I have bought myself a new MP3 player, I used to connect to the old one through the USB port with 'sudo mount /media/MP3'. The line in fstab is '/dev/sdb1 /media/MP3 vfat iocharset=utf8,umask=000 0 0' and it worked perfectly.

I bought the new MP3 and with the same setup all I can get is ' mount: special device /dev/sdb1 does not exist'.
I connected it to a Windows system and I can see all the folders, transfer data and everything looks OK, it works exactly as it should.

Any ideas how to get it to work in Linux??

---

### Post by m0biu5 on 2007-12-04
After you plug in your MP3 player, before you try to mount it, can you execute the command  ```
dmesg | tail
``` and paste that here?

---

### Post by Niloc on 2007-12-04
colin@Desktop:~$ dmesg | tail
[ 8209.577933] sdb: assuming drive cache: write through
[ 8209.581797] SCSI device sdb: 1928960 512-byte hdwr sectors (988 MB)
[ 8209.582920] sdb: Write Protect is off
[ 8209.582924] sdb: Mode Sense: 00 12 00 00
[ 8209.582926] sdb: assuming drive cache: write through
[ 8209.582930]  sdb: unknown partition table
[ 8209.589815] sd 17:0:0:0: Attached scsi removable disk sdb
[ 8209.589866] sd 17:0:0:0: Attached scsi generic sg1 type 0
[ 8209.593838] sd 17:0:0:1: Attached scsi removable disk sdc
[ 8209.593886] sd 17:0:0:1: Attached scsi generic sg2 type 0
colin@Desktop:~$ 

Hope you can make sense of this!!

---

### Post by m0biu5 on 2007-12-04
Hmm, the part I don't know about is "sdb: unknown partition table". Do you know what format the mp3 player is in? I would assume FAT32. Try changing fstab to say sdb instead of sdb1.

---

### Post by Niloc on 2007-12-05
Tried that but no difference, so I changed it back.
I can see the disk using GParted and it is all shown as 'unallocated', how can I allocate it to something?

---

### Post by Niloc on 2007-12-05
I fixed it, my Swedish mate with whom I have been hasseling in parallel, suggested I look at 'Removable Devices & Media', I set 'Mount Removable Devices when Hotplugged' and away it went....
Thank you for your assistance...

Colin

---

