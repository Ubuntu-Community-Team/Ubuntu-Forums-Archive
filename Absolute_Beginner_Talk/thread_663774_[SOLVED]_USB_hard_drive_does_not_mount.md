---
title: "[SOLVED] USB hard drive does not mount"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by VON_CAPO on 2008-01-10
I have a external hard drive already formatted as EXT3 which was mounting OK until I played with the "Properties" dialog of the icon located on the Desktop.

This dialog has a Tab called "Volume" where you can change the "Mount Point"; so, I changed this mount point to "/media/USB_500GB".

Now, when I plug the disk a dialog pop up complaining "Cannot mount volume" as shown in the following screenshot:  
[[IMG]http://img293.imageshack.us/img293/5405/screenshotfl0.th.png[/IMG]](http://img293.imageshack.us/my.php?image=screenshotfl0.png)

I was browsing some similar threads but I did not get any solution (or I was unable to understand them).

Also, I was looking for a Disk Manager and I installed "KDiskFree", but it does not offer any option to tweak the mount points.

Any idea? :confused:

---

### Post by Hospadar on 2008-01-10
I think when you specify the mount point in that tab, it assumes you are putting it in /media, so you don't need to say /media/USB_500GB, but rather just USB_500GB

I think when you specify a mount point in that tab, it puts a line in your /etc/fstab for that drive, so probably if you delete that line (or change the mount point) you can resolve the problem.

Could you post a copy of you /etc/fstab file?

---

### Post by Hayden on 2008-01-10
First plug the drive in, then open the terminal and get a list of your partition tables.

```
sudo fdisk -l
```

Look for your external drive, it will be something like /dev/sdbX or /dev/sdcX etc. X is what ever number you see. Now mount the drive.

```
sudo mount /dev/sdbX /media/USB_500GB
```

---

### Post by VON_CAPO on 2008-01-10
Here is my fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=46d6fbb6-6ffa-46d8-9386-cf74fecbfc1a /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda3
UUID=505f1cd3-1ca5-4c98-bbbc-04f11c5a3022 /home           ext3    defaults        0       2
# /dev/sda5
UUID=a5fc8c1b-8669-400b-bfaf-442b06385d71 /media/disk1    ext3    defaults        0       2
# /dev/sdb1
-UUID=166f5182-9420-45c1-abe4-863762cff9d2 /media/disk2    ext3    defaults        0       2
# /dev/sdc1
UUID=b9e67ddb-fe64-4de5-a343-605fda8d35f3 /media/disk3    ext3    defaults        0       2
# /dev/sda6
UUID=2ddead3b-aeeb-4f67-a354-b6279bcdd9e1 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
```

Where:
---   " / ", " /home " and " /media/disk1" are partitions located in a 160GB disk (First disk, internal SATA)

---  " /media/disk2 " is located in another 160GB disk (Second disk, internal SATA)

---  " /media/disk3 is located in a 250GB disk (Third disk, internal ATA)

Also I have 2 external USB hard drives:

--- 1st one is a 750GB, which is already mounted and working OK, and it is mounted at:
   "/media/disk"

--- And a second USB of 500GB** (this is the disk with the problem)**, that it was originally mounted at: 
  "/media/disk-1"

---

### Post by Glendon on 2008-01-10
I made this same mistake and got the same error. 

I fixed it by mounting the external drive at the command line and then removing the entry I made in Properties that broke it in the first place. Then, I unmounted at the command and then re-cycled the power on the external hard drive. Ubuntu auto-mounted just like before.

---

### Post by VON_CAPO on 2008-01-10
Ok, I did the following:
```
sudo fdisk -l
```
and this is the output:
```

fab@top:~$ sudo fdisk -l
[sudo] password for fab:

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x88837ca2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30515   245111706   83  Linux

Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb61ab61a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2432    19535008+  83  Linux
/dev/sdb2            8511       19452    87891615    5  Extended
/dev/sdb3            2433        8510    48821535   83  Linux
/dev/sdb5            8511       19209    85939686   83  Linux
/dev/sdb6           19210       19452     1951866   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfe15fe15

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       19457   156288321   83  Linux

Disk /dev/sdd: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       91201   732572001   83  Linux

Disk /dev/sde: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8d399bc0

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       60801   488384001   83  Linux
```

So, I did:

```
fab@top:~$ sudo mount /dev/sde1 /media/USB_500GB
mount: mount point /media/USB_500GB does not exist
```

Now, how can I create a "mount point'?

---

### Post by Falc7 on 2008-01-10
I have the same problem

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x452f1e71

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9305    74738258    7  HPFS/NTFS
/dev/sda2           18596       19457     6924015    7  HPFS/NTFS
/dev/sda3            9306       18211    71537445   83  Linux
/dev/sda4           18212       18595     3084480    5  Extended
/dev/sda5           18212       18595     3084448+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    7  HPFS/NTFS


This is my fstab, what should i type? the things i tried typing in didn't work

---

### Post by logos34 on 2008-01-10
> **VON_CAPO said:**
> 
Now, how can I create a "mount point'?

sudo mkdir /media/USB_500GB

---

### Post by VON_CAPO on 2008-01-10
Wonderful!! 
```
fab@top:~$ sudo mkdir /media/USB_500GB
fab@top:~$ sudo mount /dev/sde1 /media/USB_500GB
```
It works!!
Thank you so much to everybody   :):):)

**EDIT:** I learned something new. Thanks.:guitar:

---

### Post by Hayden on 2008-01-10
You Welcome. :)

---

