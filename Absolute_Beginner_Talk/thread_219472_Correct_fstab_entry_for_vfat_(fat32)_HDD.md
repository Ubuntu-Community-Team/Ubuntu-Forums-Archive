---
title: "Correct fstab entry for vfat (fat32) HDD?"
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by u.b.u.n.t.u on 2006-07-20
Hi,

I have added an extra HDD to act as a transfer device between ext3 and ntfs.

I understand that vfat doesn't handle permissions. I don't have permission within ubunbtu to transfer data to my vfat (fat32) HDD.

What is the entry in fstab that I need. I tried a few that I found and nothing seems to work.

Thanks.

---

### Post by gerbman on 2006-07-20
Here's the fstab entry for my FAT32 drive, which I have full read/write permission for:```
/dev/hdb1       /mnt/hd2        vfat    defaults,uid=gerb    0       2
```where "gerb" is the name of my account in Ubuntu.

---

### Post by orb9220 on 2006-07-20
Unless you make a folder called hd2 in your /mnt directory it won't know what 
to do.

goto in nautilus the /mnt directory and create a folder called hd2
Then reboot.

mine is : 
/dev/hdd1     /drives/hdd1     vfatdefaults,utf8,umask=007,gid=46 0    0

so I have a folder in /drives called hdd1

Hope this helps

---

### Post by u.b.u.n.t.u on 2006-07-20
This works, thank you!

```
/dev/hdc1       /media/vfat     vfat    defaults,utf8,umask=007,gid=46 0 0
```

---

