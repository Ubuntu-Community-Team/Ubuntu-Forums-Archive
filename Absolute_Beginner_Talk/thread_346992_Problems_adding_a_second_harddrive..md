---
title: "Problems adding a second harddrive."
date: 2007-01-26
forum: Absolute Beginner Talk
---

### Post by gu014 on 2007-01-26
Hello,
I am attempting to add a new harddrive. The HD is IDE and is running as a slave on the primary ide channel.

gparted does not show the drive and when running gparted yields the following errors:

"Disk /dev/hdb doesn't contain a valid partition table"

```
sudo fdisk -l
``` produces ```
Disk /dev/hdb doesn't contain a valid partition table
```

Any help would be greatly appreciated.  Thank you.

---

### Post by rsambuca on 2007-01-26
Did you set the jumper to "slave"?

---

### Post by taurus on 2007-01-26
Go into the BIOS and see if it reports the right capacity for your slave drive at all.

---

### Post by gu014 on 2007-01-26
The drive is indeed recognized by the bios as the proper size and also as the primary slave.

I tried setting the jumper as cable select as well as no jumper with the same results.

Any suggestions?

---

### Post by tagginannie on 2007-01-26
> **gu014 said:**
> Hello,
I am attempting to add a new harddrive. The HD is IDE and is running as a slave on the primary ide channel.

gparted does not show the drive and when running gparted yields the following errors:

"Disk /dev/hdb doesn't contain a valid partition table"

```
sudo fdisk -l
``` produces ```
Disk /dev/hdb doesn't contain a valid partition table
```Any help would be greatly appreciated.  Thank you.

If you have Windows try to set the drive up with a FAT 32 partition. When your
 done boot back in to Linux and see if you have any more trouble with Gparted
 and Fdisk. 

Suzy

---

### Post by Threbus5 on 2007-01-26
Hi,

"Disk /dev/hdb doesn't contain a valid partition table" - ok, believe the response, assume that the drive is not partitioned.

After using fdisk to partition and format the drive did you still receive that fdisk -l response?  As someone suggested a FAT32 partition may be a good starting point. However the drive can just as easily be formatted/partitioned for Linux.

There is a tutorial about adding a pen drive or usb drive as a second disk that may be helpful. 

If you still have a problem I should be able to find the tutorial for fdisk and send it to you - it is my help file repositories and they are presently unaccessible.

take care (if you need the howto, send a private post to me)

---

