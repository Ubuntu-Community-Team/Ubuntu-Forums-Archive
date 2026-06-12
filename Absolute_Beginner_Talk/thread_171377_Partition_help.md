---
title: "Partition help"
date: 2006-05-06
forum: Absolute Beginner Talk
---

### Post by Suslisko on 2006-05-06
I have a fat 32 partition on my HD. Ubuntu did mount it under /media/hdc8 but i cant change the owner so i can't write to it. I did try chown but it didnt work. Any ideas ?

---

### Post by aysiu on 2006-05-06
You can't *chown* FAT32 partitions. Copy and paste these commands into the terminal ```
sudo umount /dev/hdc8
sudo mkdir /fat_partition
sudo cp /etc/fstab /etc/fstab_backup
sudo nano /etc/fstab
``` Find this line ```
/dev/hdc8 /media/hdc8 vfat defaults 0 0
``` and change it to ```
/dev/hdc8 /fat_partition vfat iocharset=utf8,umask=000 0 0
``` Save (control-x), confirm (y), exit (Enter). ```
sudo mount -a
```

---

### Post by Suslisko on 2006-05-06
Many thanks. It worked just fine.

---

