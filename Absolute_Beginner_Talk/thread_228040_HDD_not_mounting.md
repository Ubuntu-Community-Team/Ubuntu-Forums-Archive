---
title: "HDD not mounting"
date: 2006-08-02
forum: Absolute Beginner Talk
---

### Post by snellbag on 2006-08-02
Hi all - I'm a newbie to the world of Linux so I thought I'd give Ubuntu a try. I've managed to install it fine, however, my 2 HDDs are inaccessible; they show up, but do not mount. I'm not really sure what to do, any help would be greatly appreciated.

Thanks

---

### Post by nixclusive on 2006-08-02
show up where? try posting the output of 'fdisk -l' here.
Open the terminal from the menu, At the prompt, type:
```

sudo fdisk -l
```

copy and paste the output here.

---

### Post by snellbag on 2006-08-02
Disk /dev/hdc: 40.9 GB, 40982151168 bytes
255 heads, 63 sectors/track, 4982 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   ID  System
/dev/hdc1   *           1         412     3309358+   b  W95 FAT32
/dev/hdc2             413        4111    29712217+   f  W95 Ext'd (LBA)
/dev/hdc5             413        4111    29712186    b  W95 FAT32

Disk /dev/hdd: 10.2 GB, 10242892800 bytes
255 heads, 63 sectors/track, 1245 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   ID  System
/dev/hdd1               1         641     5148801    c  W95 Fat32 (LBA)
/dev/hdd2   *         642        1216     4618687+  83  Linux
/dev/hdd3            1217        1245      232942+   5  Extended
/dev/hdd5            1217        1245      232911   82  Linux swap / Solaris

---

### Post by snellbag on 2006-08-02
hmm crap the alignment on that post was a bit off, I'm using Ubuntu on a different computer next to me so I can't just copy and paste.

---

### Post by nixclusive on 2006-08-02
> **snellbag said:**
> Disk /dev/hdc: 40.9 GB, 40982151168 bytes
255 heads, 63 sectors/track, 4982 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   ID  System
/dev/hdc1   *           1         412     3309358+   b  W95 FAT32
/dev/hdc2             413        4111    29712217+   f  W95 Ext'd (LBA)
/dev/hdc5             413        4111    29712186    b  W95 FAT32

Disk /dev/hdd: 10.2 GB, 10242892800 bytes
255 heads, 63 sectors/track, 1245 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   ID  System
/dev/hdd1               1         641     5148801    c  W95 Fat32 (LBA)
/dev/hdd2   *         642        1216     4618687+  83  Linux
/dev/hdd3            1217        1245      232942+   5  Extended
/dev/hdd5            1217        1245      232911   82  Linux swap / Solaris

looks like you have ubuntu installed on hdd2 with a swap partition on hdd5. You can mount any of the windows drives (except those that say 'Extended') to any directory you want. For temporary testing, mount any drive (eg. hdd1) on /mnt by issuing the folowing in the terminal:
```
sudo mount -r /dev/hdd1 /mnt/
```

The '-r' flag ensures that the filesystem is mounted read-only. If you are faced with any error, try adding a '-t' flag to specify the filesystem type:
```
sudo mount -r -t vfat /dev/hdd1 /mnt/
```

where 'vfat' specifies that the partition contains a FAT file system.

If you'd like your partitions to automount on startup, you'll have to edit the file: /etc/fstab

Paste the output of the following command here:
```
cat /etc/fstab
```

This will enable be to help you better. :)

---

### Post by nixclusive on 2006-08-02
btw there should be a guide to automount your filesystems somewhere in these forums.

[http://ubuntuforums.org/showthread.php?t=186638&highlight=automounting](http://ubuntuforums.org/showthread.php?t=186638&highlight=automounting)

---

### Post by snellbag on 2006-08-02
I temporarily mounted that partition, and yes it is now mounted and read-only. is there a way to make them writeable? dump of /etc/fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc            /proc         proc   defaults  0      0
/dev/hdd2       /             ext3   defaults, errors=remount-ro 0    1
/dev/hdd5       none          swap   sw        0      0
/dev/hda        /media/cdrom0 udf,iso9660 user,noauto   0    0

---

### Post by nixclusive on 2006-08-02
> **snellbag said:**
> I temporarily mounted that partition, and yes it is now mounted and read-only. is there a way to make them writeable? dump of /etc/fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc            /proc         proc   defaults  0      0
/dev/hdd2       /             ext3   defaults, errors=remount-ro 0    1
/dev/hdd5       none          swap   sw        0      0
/dev/hda        /media/cdrom0 udf,iso9660 user,noauto   0    0

remove the '-r' flag:
```
sudo mount /dev/hdd1 /mnt/
```

For automount:
```
sudo mkdir /media/{hdc1,hdc5,hdd1}
sudo cp /etc/fstab /etc/fstab_backup
sudo cat >> /etc/fstab << EOF
/dev/hdc1        /media/hdc1 vfat defaults 0 0
/dev/hdc5        /media/hdc5 vfat defaults 0 0
/dev/hdd1        /media/hdd1 vfat defaults 0 0
EOF
sudo mount -a
```

This should mount your drives hdc1,hdc5 and hdd1 to /media/ folders respectively. Further, it should also automount these partitions on reboot.

---

### Post by snellbag on 2006-08-02
thanks - followed your instructions, but on entering EOF the 2nd time I got this error: [COLOR="Red"]bash: /etc/fstab: Permission denied[/COLOR]
[COLOR="Black"]...what did I do wrong...?[/COLOR]

---

### Post by snellbag on 2006-08-02
thanks - followed your instructions, but on entering EOF the 2nd time I got this error: [COLOR="Red"]bash: /etc/fstab: Permission denied[/COLOR]
[COLOR="Black"]...what did I do wrong...?[/COLOR]

---

### Post by givré on 2006-08-02
Just edit your fstab with 
```
gksu gedit /etc/fstab
```

---

### Post by snellbag on 2006-08-11
erm...i edited the /etc/fstab and now ubuntu does not load. I get this error:

"Could not start the X server (your graphical environment) due to some internal error. Please contact your system administrator or check your syslog to diagnose. In the meantime this display will be disabled. Please restart GDM when the problem is corrected."

help!

---

### Post by nixclusive on 2006-08-11
> **snellbag said:**
> erm...i edited the /etc/fstab and now ubuntu does not load. I get this error:

"Could not start the X server (your graphical environment) due to some internal error. Please contact your system administrator or check your syslog to diagnose. In the meantime this display will be disabled. Please restart GDM when the problem is corrected."

help!

/etc/fstab has nothing to do with gdm crashing! However you can try to reload it. Press Ctrl+Alt+F1 and login at the text prompt. Enter:
```
sudo /etc/init.d/gdm start
```If the X-Server problem still persists...wait a while for experts to walk in here. Thanks.

---

### Post by snellbag on 2006-08-11
i assure you I did nothing else to provoke it! after entering that line, is the display supposed to restore automatically?

---

