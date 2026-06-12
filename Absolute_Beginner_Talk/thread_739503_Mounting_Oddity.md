---
title: "Mounting Oddity"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by crashcoredump on 2008-03-29
So I purchased a new second drive to add to my configuration and all went well. But after a reinstall where I chose to NOT re-initalize the drive it never made it into mt /etc/fstab.
Here is what the file looks like.

```
zao@Painhu:~$ sudo vim /etc/fstab 
[sudo] password for zao:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=bf3d11c1-5818-4f7e-993f-0ce16ff3c246 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=2ca58450-54a5-4356-a19c-e42a1e2192dc none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
zao@Painhu:~$ 

```


Now each time I reboot I need to: sudo mount /dev/hbd /media/Storage to be able to get the drive again. There is already an entry for hdb but it mounts it as a CDROM?

If I put it in my fstab what should the entry look like?

/media/Storage is the directory I made to access the volume.


Thanks

-J

---

### Post by dsauxier on 2008-03-29
Comment out the existing line for /dev/hdb by putting "#" in front of it.
Then add a new one (I'm assuming it's /dev/hdb1)
```

#/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdb1 /media/Storage     auto     defaults        0       2
```

This also implies that your cdrom is now elsewhere.
Trial and error may work as well as anything, or you can try 
```
 sudo fdisk -l
```
most likely you need to change /dev/hdb to /dev/hdc
```
#/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```

 
FYI, I'm leaving soon, so I won't be able to post any more on this today.

---

### Post by crashcoredump on 2008-05-11
So I edited my fstab and have yet to reboot.
Since my first install of the new 1TB drive and the choice to make it one partition there are always been some issues with it.

Gparted seems to think there is an issue that cannot be repaired but the volume works fine once mounted.

Here is the output of fdisk.

Any ideas


```
  
zao@Painhu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9aa12711

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13995   112414806   83  Linux
/dev/sda2           13996       14593     4803435    5  Extended
/dev/sda5           13996       14593     4803403+  82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdg: 8253 MB, 8253341696 bytes
16 heads, 32 sectors/track, 31484 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x18f595e6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1       31484     8059888    b  W95 FAT32
zao@Painhu:~$ 


```


Here is the edited file,

```

zao@Painhu:~$ cat /etc/fstab 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=bf3d11c1-5818-4f7e-993f-0ce16ff3c246 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=2ca58450-54a5-4356-a19c-e42a1e2192dc none            swap    sw              0       0
#/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdc         /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
 
/dev/hdb /media/Storage          auto     defaults             0     2
zao@Painhu:~$ 



```

---

