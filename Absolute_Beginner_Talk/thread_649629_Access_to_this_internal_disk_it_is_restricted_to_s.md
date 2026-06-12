---
title: "Access to this internal disk it is restricted to system administrators"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by muntaser on 2007-12-25
Please help me...I'm using Ubuntu 7.06, I'm getting a little frustrated at receiving the following message:
"access to internal disk it is restricted to system administrators for security reasons"

So when I'm trying to open it from "Computer" , it asks for a password. After giving the password it works properly.But I don't want to give my password every time I try to log in to this disk.
 Here is my fstab file...plz help me to solve this problem.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=219d7ec5-01af-4f9c-9e0f-a84de35d3d8f /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=DC7073757073556C /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdc1
UUID=f3d0e989-4325-4743-9921-8524e4ad80d3 /media/hdc1     vfat    defaults,user        0       2
# /dev/hda3
UUID=f513a24b-5f40-daa1-7e96-6e61a7c5edbd none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


note: the problem in hdc1 disk

---

### Post by taurus on 2007-12-25
Instead of mounting your vfat like what you have in /etc/fstab right now,

```

UUID=f3d0e989-4325-4743-9921-8524e4ad80d3 /media/hdc1 vfat defaults,user 0 2

```
you should probably be better off mounting it like this.

```

UUID=f3d0e989-4325-4743-9921-8524e4ad80d3  /media/hdc1  vfat  iocharset=utf8,umask=000  0  0
```

You can edit your /etc/fstab with

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/fstab
```

Don't forget to reboot after you've made the changes.

---

### Post by muntaser on 2007-12-25
Hi
Unfortunately, It didnt work, I change the line as you said, But it is still asking for my password.

---

### Post by rkd on 2007-12-25
Could it be that the UUID given in /etc/fstab for that partition doesn't match what is on the disk?  I think you can show the UUIDs on the disk with fdisk -l.

I'm just tossing out a guess here. I don't know much about this, so I might be completely on the wrong track.

---

### Post by muntaser on 2007-12-25
here it is the fdisk -l of my hard disk

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4844    38909398+   7  HPFS/NTFS
/dev/hda2            4845        9697    38981722+  83  Linux
/dev/hda3            9698        9729      257040   82  Linux swap / Solaris

Disk /dev/hdc: 20.5 GB, 20520493056 bytes
255 heads, 63 sectors/track, 2494 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1        2494    20033023+   b  W95 FAT32

how can this help me to solve my problem?

---

### Post by taurus on 2007-12-25
Try

```
sudo umount /media/hdc1
sudo mount -t vfat /dev/hdc1 /media/hdc1 -o umask=000
ls -la /media/hdc1
```

---

### Post by rkd on 2007-12-25
Sorry, my mistake.  fdisk doesn't show the UUIDs.  It is some other command that shows the UUIDs on the disk partitions, but I can't recall right now what that command is.

---

### Post by LaRoza on 2007-12-25
> **rkd said:**
> Sorry, my mistake.  fdisk doesn't show the UUIDs.  It is some other command that shows the UUIDs on the disk partitions, but I can't recall right now what that command is.
```

ls /dev/disk/by-uuid -alh

```

Isn't it obvious? (:))

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by rkd on 2007-12-25
@LaRoza: Obvious?  Sure.  As obvious as any Unix command.

Seriously, Thanks for the reminder.

@muntaser: Please post the result of the command LaRoza gave us and we'll see whether that shows us the problem.

---

