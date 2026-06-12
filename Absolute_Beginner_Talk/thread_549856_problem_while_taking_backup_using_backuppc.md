---
title: "problem while taking backup using backuppc"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by varunanohar on 2007-09-13
hi all

i'm having problem in backuppc it gives the erroe mentioned below and 
show backup in progress and time is unlimited means taking 


so much time and after that error so wht shd i do plz reply soon .

ERROR:

Running: /usr/bin/ssh -q -x -l root 

mis.nuchem.com /usr/bin/rsync --server 
--sender --numeric-ids --perms --owner --group --devices --links --times 

--block-size=2048 --recursive --ignore-times . /home/nuchemadmin/
Xfer PIDs are now 10829


Read EOF: Connection reset by peer
Tried again: got 0 bytes
Done: 0 files, 0 bytes
Got fatal error during xfer (Unable to read 4 bytes)

Backup aborted (Unable to read 4 bytes)



Regards/-

Varuna Nohar

---

### Post by Dirk_DC on 2007-10-07
For Edgy or Feisty clients you need to replace --device by -D in the definition of the rsync commands in /etc/backuppc/config.pl, otherwise clients refuse to back up.

---

