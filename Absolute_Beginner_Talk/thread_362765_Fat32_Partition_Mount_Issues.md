---
title: "Fat32 Partition Mount Issues"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by WallabyWannabe on 2007-02-16
I found a guide showing how to mount a FAT32 partition with full permissions. It says to use this command:

sudo mount /dev/sdb1 /media/MyDocuments/ -t -vfat -o iocharset=utf8,umask=000

However I get the error:

mount: unknown filesystem type '-vfat'

"sudo fdisk -l" tells me the drive is W95 FAT32. This partition is a full 250gig harddrive, and I partitioned it using the partition manager that is in the Ubuntu install.


Thanks for the assistance!

---

### Post by taurus on 2007-02-16
```
sudo mount /dev/sdb1 /media/MyDocuments/ -t **vfat** -o iocharset=utf8,umask=000
```

---

### Post by WallabyWannabe on 2007-02-16
Bah~

Don't you hate when your spend 20mins on something, and then its something so small thats wrong! heh..


Thanks so much !!

---

