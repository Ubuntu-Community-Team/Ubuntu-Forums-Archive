---
title: "[SOLVED] Disk drive names change at boot"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by Stormspireiv on 2007-08-01
First of all, thanks for all help in advance.

I currently have two hard drives installed: one SCSI and one ATA133. My SCSI drive has a NTFS partition with XP on it and the Ubuntu partition with its swap partition.  The ATA133 drive just has one big NTFS partition.  I used ntfsconfig to mount both my NTFS partitions and then set up a few bookmarks and shortcuts to the folders I use regularly on those partitions.  Unfortunately, whenever I boot, the drives get reassigned. For example my /etc/fstab looks like this:
```
/dev/sdb1 /media/Windows ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda1 /media/Storage ntfs-3g defaults,locale=en_US.UTF-8 0 0
```
Whenever I boot, it (seemingly) randomly assigns which partition to call /dev/sdb1 and /dev/sda1 so sometimes it mounts correctly (with the XP partition mounted to /media/Windows and the other one mounted to /media/Storage), but other times it mounts the XP partition to /media/Storage and the other one to /media/Windows (thus breaking my shortcuts and bookmarks).

Does anyone have any idea why it is changing and how could I go about fixing it?

---

### Post by sab0403 on 2007-08-01
It's pretty confusing, indeed. Particularly because the IDE drive should be hda#, not sda/b...

I'm thinking that a little tinkering with the BIOS might help. I'm not sure what's going on though... sorry.

---

### Post by sab0403 on 2007-08-01
Oh, and also I believe a topic like this isn't suited for the "Absolute Beginners" forum. Perhaps in general help you'd get more replies?

---

### Post by Rocket2DMn on 2007-08-01
My IDE drive gets picked up as scsi for some reason, but it works, so I don't fiddle with it.
It may help if you declare the partition by UUID rather than /dev location
```
ls /dev/disk/by-uuid -alh
```
will display your drives by UUID, you can try substituting the /dev/* portion of each fstab entry with their UUID in the manner
```
UUID=123456789ABCDEF /media/Windows defaults,locale=en_US.UTF-8 0 0
```

You can, of course, reference [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131) for more details.

---

### Post by noob12 on 2007-08-01
The quick answer is this.

Running
```

sudo vol_id /dev/sda1

```
will compute a UUID (see the ID_FS_UUID in the output).  You can mount by UUID in the fstab.

---

### Post by Stormspireiv on 2007-08-01
> **Rocket2DMn said:**
> My IDE drive gets picked up as scsi for some reason, but it works, so I don't fiddle with it.
It may help if you declare the partition by UUID rather than /dev location
```
ls /dev/disk/by-uuid -alh
```
will display your drives by UUID, you can try substituting the /dev/* portion of each fstab entry with their UUID in the manner
```
UUID=123456789ABCDEF /media/Windows defaults,locale=en_US.UTF-8 0 0
```

You can, of course, reference [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131) for more details.

I changed my /etc/fstab to UUID and it (so far) works perfectly! Thanks everyone.

---

