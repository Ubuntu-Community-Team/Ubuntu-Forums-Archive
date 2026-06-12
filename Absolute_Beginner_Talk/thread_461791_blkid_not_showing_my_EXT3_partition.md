---
title: "blkid not showing my EXT3 partition"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by Doc.Caliban on 2007-06-02
I have a second internal drive in my laptop that I've used Gparted to configure with one primary partition formatted as EXT3.  According to Gparted and fdisk -l, the partion is /dev/sdb1.

I want to add it to my fstab, but I can't find the partition via blkid.  The only things that show up there are sda1 and sda5.

I also tried this by configuring the disk with an extended partition with an EXT3 file system but found the same problem.

-Doc

---

### Post by Inxsible on 2007-06-02
Could you post the output of
```
sudo fdisk -l
```
and also 
```
 gksudo gedit /etc/fstab
```

---

### Post by Doc.Caliban on 2007-06-02
```

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11661    93666951   83  Linux
/dev/sda2           11662       12161     4016250    5  Extended
/dev/sda5           11662       12161     4016218+  82  Linux swap / Solaris

Disk /dev/sdb: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       12161    97683201   83  Linux  [COLOR="Red"]The one I want to mount[/COLOR]

Disk /dev/sdc: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       36481   293033601    7  HPFS/NTFS

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       60801   488384001    7  HPFS/NTFS

```



```

:~$ blkid
/dev/sda1: UUID="24e7e574-3d81-48e3-a507-2bb3c016329b" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="dfad11fa-13c2-447d-a8ed-d5bc7789eea6" TYPE="swap" 
/dev/sdc1: TYPE="ntfs" 
/dev/sdd1: TYPE="ntfs" 

```

-Doc

---

### Post by Inxsible on 2007-06-02
and your fstab ?

Its strange that the fdisk recognizes the drive but wont give you the UUID.

Is there a reason you want the UUID, coz if you simply want to mount it, you can use the device name directly. in this case it would be /dev/sdb1.

Actually using the device name is better since it is more human readable. I have changed my fstab to have device names instead of UUIDs

---

### Post by Doc.Caliban on 2007-06-02
Shoot, sorry.  I saw that you asked for the fstab but I spaced it.  (tired, it's 3:30am here).

```

proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=24e7e574-3d81-48e3-a507-2bb3c016329b / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=dfad11fa-13c2-447d-a8ed-d5bc7789eea6 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0

```

I've tried a few mount commands but keep ending up with a read only mounting.

I'm happy to do it wihtout the UUID.

-Doc

---

### Post by Inxsible on 2007-06-02
Add this line to your fstab

```
/dev/sdb1 /media/sdb1 ext3 defaults 0 2
```

you can change the name of the mount point, if you like for eg. /media/data or /media/shared, well you get the drift.

its 3:35 am here too :)

---

### Post by Inxsible on 2007-06-02
if you want you can change the existing UUIDs for sda1 and sda5 in the fstab too
simply remove the UUID key and value pair and put in the device name :)

---

### Post by Inxsible on 2007-06-02
and in case you want to mount your NTFS drives too - if they are internal that is

you can add this line to the fstab
```
/dev/sd* /media/* ntfs-3g rw,auto,exec,user,locale=en_US.UTF-8 0 1
```

Simply replace the first star with the device name and the second star with the mount point under media.

If they are external drives -- which is what i think they are since they are 300 and 500 gb large, you should use pmount. But we shall save that for another time :)

---

### Post by Doc.Caliban on 2007-06-02
Thanks for all the info!

The NTFS drives are in fact external and are mounted with the ntfs read/write driver thing.  (sorry if that was too technical.)  :-)

/dev/sdb1 /media/Data ext3 defaults 0 2  mounted as read only again.  :-(

-Doc


Do I need to chmod something?

---

### Post by Inxsible on 2007-06-02
```
sudo chown -R <username>:<group> <device-name>
```

so assuming that your username is doc and group is doc too
```
sudo chown -R doc:doc /media/Data
```

---

### Post by Doc.Caliban on 2007-06-02
> **Inxsible said:**
> ```
sudo chown -R <username>:<group> <device-name>
```

so assuming that your username is doc and group is doc too
```
sudo chown -R doc:doc /media/Data
```

chown, chmod, choad, whatever!  :-D

Thank you, all done!

It really is easy once you know what to do.  I spent 15 years with Windows, 10 years at MS, so I know that OS inside and out.  Linux is brand new to me and it's so frustrating to know nothing, but so fun to learn.

Thanks again!

-Doc

---

