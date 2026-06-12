---
title: "mounting ntfs hd getting confusing :)"
date: 2006-02-07
forum: Absolute Beginner Talk
---

### Post by dekoffie on 2006-02-07
Hello there,

first off, I'm pretty new to linux, only had a short 1 hour intro to linux at uni once, but that's all. I installed ubuntu, all went pretty smooth (except for something about bsdutils not installing but I managed to get around that)

So, now I currently have two hard drives in my pc; one 15 gig drive, on which Ubuntu is currently installed, and a 2nd one (80 gig, slave), which is a NTFS drive currently. I don't want to format this drive because it's packed with backup material and I currently don't want to start burning or copying all these files, so..
After searching around this forum, I followed the steps as described here; 
[http://ubuntuguide.org/#automountntfs](http://ubuntuguide.org/#automountntfs)
But this does not seem to work.. After booting, my /media/windows directory is empty. When I try to unmount (sudo umount /media/windows), it says that /media/windows is already unmounted.
But, if I try to do mount /media/filez, it says;
mount: /dev/hdb already mounted or /media.windows busy.

I get a proper listing when I do fdisk -l though;
dekoffie@ubuntu:/ $ sudo fdisk -l 
Disk /dev/hda: 15.3 GB, 15367790592 bytes 
16 heads, 63 sectors/track, 29777 cylinders 
Units = cylinders of 1008 * 512 = 516096 bytes 

      Device Boot       Start        End        Blocks      Id        System
/dev/hda1 * 1 28783 14506600+ 83 Linux 
/dev/hda2 28784 29777 500976 f W95 Ext'd (LBA) 
/dev/hda5 28784 29777 500944+ 82 Linux swap 

Disk /dev/hdb: 80.0 GB, 80026361856 bytes 
255 heads, 63 sectors/track, 9729 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 

      Device Boot       Start        End        Blocks      Id        System /dev/hdb1 1 9728 78140128+ 7 HPFS/NTFS

So, does anyone get any tips for this linux newbie? ;)

Thanks in advance!

---

### Post by aysiu on 2006-02-07
Please post the output of these two commands: ```
df -h
cat /etc/fstab
```

---

### Post by dekoffie on 2006-02-07
```
**df -h**:
Password:
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              14G  1,7G   12G  13% /
tmpfs                  63M     0   63M   0% /dev/shm

```

```
**cat /etc/fstab**:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdb        /media/windows  ntfs   nls=utf8,umask=0222 0       0

```

Hope that might help in finding any reasons.. :)

---

### Post by kont.raen on 2006-02-07
Hi dekoffie,

I think the mistake is in this line of the fstab you posted :

```

/dev/hdb        /media/windows  ntfs   nls=utf8,umask=0222 0       0

```

The problem is, that the whole disk is used as "source" instead of the partition on this disk/device. Iirc from your first post, fdisk -l told us that the ntfs partition is hdb1, so you have to change the line quoted above in the /etc/fstab. Therefore do the following :

1.) open up a terminal

2.) make a backup of your fstab - just in case ;) 
```

sudo cp /etc/fstab /etc/fstab-original

```

3.) open and edit the fstab with an editor of your choice, though I would suggest gedit if you are not yet to experienced with editors like vim, nano etc.
```

sudo gedit /etc/fstab

```
Once the file is loaded, find the line quoted above and change it into
```

/dev/hdb1       /media/windows  ntfs   nls=utf8,umask=0222 0       0

```

4.) Save the changes and then mount the partition.

That ought to do the trick

---

### Post by dekoffie on 2006-02-07
kont.raen and aysiu, thank you both very much for the help!
I got it working now, yay :)

---

