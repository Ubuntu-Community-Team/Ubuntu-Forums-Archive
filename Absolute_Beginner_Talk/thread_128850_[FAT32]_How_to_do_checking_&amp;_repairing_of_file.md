---
title: "[FAT32] How to do checking &amp; repairing of filesystem &amp; also disk surface for FAT32 ?"
date: 2006-02-12
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2006-02-12
Thank you very much,

Greetz

Pat

---

### Post by phen on 2006-02-12
first, you have to know the device name of your fat32 partition. it should be something like /dev/hda1 or /dev/hdb1 etc...

you get a list of your mounted drives by open up a console and type
cat /etc/mtab
or
df -h

now type
sudo fsck.vfat -ar /dev/hda1

type man fsck.vfat for more information on the -ar options. i dont remember exactly...

---

### Post by patrick295767 on 2006-02-12
Thank you very much, 

It will work !! You provided me enough information to make it !

Greetings from belgium !

Pat'

---

