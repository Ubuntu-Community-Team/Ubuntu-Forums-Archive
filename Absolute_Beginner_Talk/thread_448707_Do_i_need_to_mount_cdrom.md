---
title: "Do i need to mount cdrom?"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by anon1234 on 2007-05-19
When i go to, Places - Computer. I see the two cd / dvd drives, one being a dvd drive the other being a cd-rw.

The dvd drive was used to install ubuntu, it seems to work fine. Although, the cd-rw drive isn't working. Whenever i try to eject the drive by hitting the eject button on the drive i get "Cannot Eject Volume".

Whenever i click the drives icon i get, "Unable to Mount Media".

I load up K3B to try and burn a cd and my dvd drive shows up but not my cd-rw.

Do i need to mount the drive before it will work? The drive has been in the pc since the ubuntu install.


Just wondering why the dvd drive works and i never mounted it but the cd-rw doesn't.

---

### Post by Rab22 on 2007-05-19
The problem is probably in your /etc/fstab  -- please post the contents of this file.

Chances are that the CD-RW drive is referencing the wrong device.

---

### Post by anon1234 on 2007-05-19
/etc/fstab contents:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=9aa2d3ea-f8de-4a62-8463-e6984a006a48 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda3
UUID=a0356242-ca3b-4e49-b7be-18bfd06b6a00 /home           ext3    defaults        0       2
# /dev/hda5
UUID=84982B48982B3856 /media/hda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb1
UUID=6EBC3820BC37E16F /media/hdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda4
UUID=c86ee695-ef94-4748-862c-d46a20e54d6b none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0

```

---

### Post by Rab22 on 2007-05-19
> **chillinhh said:**
> /etc/fstab contents:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=9aa2d3ea-f8de-4a62-8463-e6984a006a48 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda3
UUID=a0356242-ca3b-4e49-b7be-18bfd06b6a00 /home           ext3    defaults        0       2
# /dev/hda5
UUID=84982B48982B3856 /media/hda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb1
UUID=6EBC3820BC37E16F /media/hdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda4
UUID=c86ee695-ef94-4748-862c-d46a20e54d6b none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0

```

From what it looks like your /etc/fstab looks correct.  Are you sure the drive works properly?

---

