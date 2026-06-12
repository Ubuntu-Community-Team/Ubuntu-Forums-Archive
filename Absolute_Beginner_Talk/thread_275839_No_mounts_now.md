---
title: "No mounts now?"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by creigscofield on 2006-10-11
I recently reinstalled ubuntu.  when I did so I made a 20gig extended partition and made a 2 gig FAT for exchanging files then let the installer have at the rest. Now i cant open any of my non ext3 partitions. last time all my ntfs and fat32 partitions would appear on the desktop on startup the same way a usb flash does when plugged in. now i cant even open them when i go to computer, it says it cant open because they are non removeable????](*,)  does ubuntu not like being on a logical drive instead of a primary partition?

---

### Post by bodhi.zazen on 2006-10-11
> **creigscofield said:**
> I recently reinstalled ubuntu.  when I did so I made a 20gig extended partition and made a 2 gig FAT for exchanging files then let the installer have at the rest. Now i cant open any of my non ext3 partitions. last time all my ntfs and fat32 partitions would appear on the desktop on startup the same way a usb flash does when plugged in. now i cant even open them when i go to computer, it says it cant open because they are non removeable????](*,)  does ubuntu not like being on a logical drive instead of a primary partition?

No, you may not have set up the partitions at the time of install.

Can you post /etc/fstab and the output of```
sudo fdisk -l
```

---

### Post by creigscofield on 2006-10-12
sure it generated this
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1           6       48163+  de  Dell Utility
/dev/hda2   *           7        6888    55279665    7  HPFS/NTFS
/dev/hda3            6889        9318    19518975    5  Extended
/dev/hda4            9319        9729     3301357+  db  CP/M / CTOS / ...
/dev/hda5            6889        7149     2096451    b  W95 FAT32
/dev/hda6   *        7150        9225    16675438+  83  Linux
/dev/hda7            9226        9318      746991   82  Linux swap / Solaris

Disk /dev/sda: 513 MB, 513277952 bytes
9 heads, 40 sectors/track, 2784 cylinders
Units = cylinders of 360 * 512 = 184320 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2785      501131+   6  FAT16

---

### Post by Kateikyoushi on 2006-10-12
We also need to see your fstab to know how to modify it.
Copy the output of the following line.

```
cat /etc/fstab
```

---

### Post by creigscofield on 2006-10-12
Here you go:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda6       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda7       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by bodhi.zazen on 2006-10-12
first make your mount points:```
sudo mkdir /mnt/windows /mnt/fat32 /mnt/sda1
```

Of course you can change the mout points to what you will, you just have to change them in fstab as well.

Now, ```
sudo cp /etc/fstab /etc/fstab.bak
sudo gedit /etc/fstab
```
Paste the following into fstab:
> proc /proc proc defaults 0 0
/dev/hda6 / ext3 defaults,errors=remount-ro 0 1
/dev/hda7 none swap sw 0 0
/dev/hdb /media/cdrom0 udf,iso9660 user,noauto 0 0

# Windows
/dev/hda2  /mnt/windows ntfs auto,defaults,users 0 0

# FAT 32
/dev/hda5 /mnt/fat32 vfat auto,defaults,users 0 0
/dev/sda1 /mnt/sda1  vfat auto,defaults,users 0 0
Save and exit gedit.
```
mount -a
```

Your ntfs will be ro. If you want rw: [url=http://ubuntuforums.org/showthread.php?t=217009
][color=olive]ntfs-3g[/color][/url]

---

