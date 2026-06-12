---
title: "Can't write to fat32 partition?"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by lemonsCC on 2006-12-18
I am trying to write (copy files) to my fat32 permission but I am getting an error stating that I don't have permission to write to it.  I tried chmod/chowing the partition, changing fstab to "user, auto, rw" and root nautilius (changing the permissions).  None of these did anything.  Please help.

Fstab looks like this:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       /home           ext3    defaults        0       2
/dev/hda3       /media/hda3     ntfs    defaults        0       0
/dev/hda7       /media/hda7     vfat    user,rw,auto        0       0
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

cp error is this:
```
cp: cannot create regular file `/media/hda7/Chem.svg': Permission denied
```

---

### Post by Caracal on 2006-12-18
I might be wrong, but i thought you could only write to NTFS drives?

---

### Post by absinthe on 2006-12-18
> **Caracal said:**
> I might be wrong, but i thought you could only write to NTFS drives?

No no, you CAN'T write to NTFS drives natively.

---

### Post by bodhi.zazen on 2006-12-18
Unmount the fat partition.

Edit fstab:> /dev/hda7  /media/hda7  vfat  user,auto,umask=000  0  0

Re-mount: ```
mount /media/hda7
```

Should now be good to go ! 8)

---

