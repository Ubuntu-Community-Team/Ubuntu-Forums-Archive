---
title: "Mounting logical drive at startup"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by brander on 2006-11-21
Hi, I can get my logical drive hda5 to mount and be read/write in terminal, but would like to add it to fstab to make it this way always. To mount it using su I put:

mount -t ext3 /dev/hda5 /mnt/Ddrive/
sudo chmod -R 777 /mnt/Ddrive

My fstab is this:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=3cdf2583-3be0-4015-94b2-4f93d960f27c /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda2
UUID=fc0cd700-3cb4-4f07-bef0-7acd06309d22 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

It looks like a UUID is required, can anyone tell me exactly what to do here please?

---

### Post by Verminox on 2006-11-21
I guess adding the following should suffice:

/dev/hda5 /mnt/Ddrive  ext3  defaults 0 0

Well, it worked for my FAT and NTFS partitions at least anyway.

---

### Post by taurus on 2006-11-21
> **Verminox said:**
> I guess adding the following should suffice:

/dev/hda5 /mnt/Ddrive  ext3  defaults 0 0

Well, it worked for my FAT and NTFS partitions at least anyway.
You may want to change the last value from 0 to 1...

```
/dev/hda5 /mnt/Ddrive  ext3  defaults 0 1
```

---

### Post by brander on 2006-11-21
Oh yes, it works. Logical really. Thank-you all.

---

