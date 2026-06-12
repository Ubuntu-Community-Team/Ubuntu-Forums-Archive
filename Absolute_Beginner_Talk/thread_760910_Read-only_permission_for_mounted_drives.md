---
title: "Read-only permission for mounted drives"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by dustoashes on 2008-04-20
I'm sorry to open up a thread that surely has its answer somewhere else, but I just don't want to mess this up. I'm using Gutsy 7.10 and I would like my hard drives to mount as read-only in Ubuntu. Can anyone explain to me how do I do this? Thanks!

---

### Post by DBrocks on 2008-04-20
I'm assuming you want to mount your slave drives as read-only. If you change your master drive (where you installed ubuntu), it will corrupt your system, and you will not be able to install anything.

---

### Post by dustoashes on 2008-04-22
I want to change the Windows partitions to read-only (excluding the one, which has the ext3/swap partition for Ubuntu).

---

### Post by muximus on 2008-04-22
if you mount them manually, using the mount command, you just need to specify the ro option
```
 mount -t <type> -ro /dev/<device name> <dir name> 
```

If the partitions are mounted at bootup, they would have entries in /etc/fstab
open the file:
```
sudo gedit /etc/fstab 
```

Add the option ro in all the lines which specify a non ext3/swap partition

Example:
Before
# Entry for /dev/sda7 :
UUID=F68CAEBF8CAE79AF /media/sda7 ntfs-3g defaults,umask=007,gid=46 0 1

After

# Entry for /dev/sda7 :
UUID=F68CAEBF8CAE79AF /media/sda7 ntfs-3g ro,gid=46 0 1

---

### Post by dustoashes on 2008-04-22
```
# /dev/sda8
UUID=A0ECD005ECCFD426 /media/sda8     ntfs    ro,gid=46 0       1
# /dev/sdb1
UUID=B0002C28002BF3CE /media/sdb1     ntfs    ro,gid=46 0       1
```

I'm guessing there's something incorrect here? I did a restard and it still allows me to delete files from these drives/partitions.

---

### Post by sisco311 on 2008-04-22
> **dustoashes said:**
> ```
# /dev/sda8
UUID=A0ECD005ECCFD426 /media/sda8     ntfs    ro,gid=46 0       1
# /dev/sdb1
UUID=B0002C28002BF3CE /media/sdb1     ntfs    ro,gid=46 0       1
```I'm guessing there's something incorrect here? I did a restard and it still allows me to delete files from these drives/partitions.

edit  the fstab options:

ro,gid=46 --> umask=333

---

### Post by dustoashes on 2008-04-25
```
# /dev/sda8
UUID=A0ECD005ECCFD426 /media/sda8     ntfs    umask=333 0       1
# /dev/sdb1
UUID=B0002C28002BF3CE /media/sdb1     ntfs    umask=333 0       1
```

Like this?

---

