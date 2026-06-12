---
title: "My 2nd hard-drive is now mounting at the wrong point, messing things up"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by inzania on 2008-04-05
I have a 2nd hard drive in the optical bay of my laptop.  It was mounting at "/media/Data" before, and everything worked well... suddenly, the media folder now contains a number of "junk" mount points - "/media/Data_" and "/media/Data__"

It seems that the computer cannot mount it at the old folders, and creates a new folder to mount the drive at instead, which messes up all the dependencies upon the folder.  Suggestions?

---

### Post by northern lights on 2008-04-05
Can you post the outputs of ```
sudo fdisk -l
``` and ```
cat /etc/fstab
```

---

### Post by inzania on 2008-04-05
Sure!  Here you are (below).  To clarify, every time I reboot, I get a new folder with an additional _ at the end of the name in the media folder.  The older folders I cannot open due to "you do not have the permissions necessary to view the folder."

sudo fdisk -l
```
Disk /dev/sda: 60.0 GB, 60011642880 bytes
240 heads, 63 sectors/track, 7752 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xed1f86f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7130    53902768+   7  HPFS/NTFS
/dev/sda2            7131        7751     4694760   12  Compaq diagnostics

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcb131e12

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       25496   204796588+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdb2           25497       30401    39399412+   7  HPFS/NTFS

```

And the fstab.  I did edit it to create the last line some time ago, but have not touched it at all recently:
```
# /etc/fstab: static file system information.
#
# <file system> 			<mount point>   <type>  <options>       	<dump>  <pass>
proc            			/proc           proc    defaults        	0       0
/host/ubuntu/disks/root.disk 		/          	ext3    loop,errors=remount-ro 	0       1
/host/ubuntu/disks/boot 		/boot           none    bind            	0       0
/host/ubuntu/disks/swap.disk 		none       	swap    loop,sw         	0       0
/dev/sdb1		 		/Data           none    bind            	0       0
/dev/sdb2		 	/Documents      none    bind            	0       0
```

thanks!

---

### Post by northern lights on 2008-04-05
> **inzania said:**
> 
```
Disk /dev/sda: 60.0 GB, 60011642880 bytes
240 heads, 63 sectors/track, 7752 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xed1f86f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7130    53902768+   7  HPFS/NTFS
/dev/sda2            7131        7751     4694760   12  Compaq diagnostics

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcb131e12

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       25496   204796588+   7  HPFS/NTFS
[COLOR="Red"]Partition 1 does not end on cylinder boundary[/COLOR].
/dev/sdb2           25497       30401    39399412+   7  HPFS/NTFS

```

This seems to be the culprit.

Not that I've encountered this error before and the behaviour of adding an underscore at every boot is something I've never seen.

"sdb1" however corresponds to "/media/Data/" and should obviously end on a cylinder boundary.

First of I'd backup the all important files (external / usb / flash drive). Then google & **** around...

---

### Post by noynac on 2008-04-05
Are you using Hardy? 

There are current threads on this issue in the Hardware and Hardy forums. There is also a report on this issue in Launchpad:

[http://ubuntuforums.org/showthread.php?t=745236](http://ubuntuforums.org/showthread.php?t=745236)

[http://ubuntuforums.org/showthread.php?t=744469](http://ubuntuforums.org/showthread.php?t=744469)

[https://bugs.launchpad.net/ubuntu/+bug/101845](https://bugs.launchpad.net/ubuntu/+bug/101845)

---

