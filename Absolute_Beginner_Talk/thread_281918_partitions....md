---
title: "partitions..."
date: 2006-10-21
forum: Absolute Beginner Talk
---

### Post by sin1984 on 2006-10-21
ok, so i partitioned my harddrive and made a 40gb partition for ubuntu. its a ext3 filesystem. when i select it and click forward, i get to the  "prepare mount points"  screen which it says
 select wich partitions you want to use for your new instiallation, and where you want to mount each of them
you must mount one partition on the root file system ("/") and you must choose at least one partition for use as swap space.

below that i have 3 mount point rows in a table and they are as follows: (the -'s are just to show empty space)

mount point-------------partition-----------------------------

/media/sda1--- partition 1 disc, usb/scsi/sata 1 (primary) [sda1]
/media/sda2--- partition 2 disc, usb/scsi/sata 1 (primary) [sda2]
/----------------- partition 3 disc, usb/scsi/sata 1 (primary) [sda3]

with a check box in reformat, in the partition 3 row

not sure what this means. and i dont want to mess anything up. so any help would be appreciated.

---

### Post by gn2 on 2006-10-21
> **sin1984 said:**
> ok, so i partitioned my harddrive and made a 40gb partition for ubuntu. its a ext3 filesystem. when i select it and click forward, i get to the  "prepare mount points"  screen which it says
 select wich partitions you want to use for your new instiallation, and where you want to mount each of them
you must mount one partition on the root file system ("/") and you must choose at least one partition for use as swap space.

below that i have 3 mount point rows in a table and they are as follows: (the -'s are just to show empty space)

mount point-------------partition-----------------------------

/media/sda1--- partition 1 disc, usb/scsi/sata 1 (primary) [sda1]
/media/sda2--- partition 2 disc, usb/scsi/sata 1 (primary) [sda2]
/----------------- partition 3 disc, usb/scsi/sata 1 (primary) [sda3]

with a check box in reformat, in the partition 3 row

not sure what this means. and i dont want to mess anything up. so any help would be appreciated.

Easiest option is to create some free space instead of an ext3 partition, and install into the free space.

---

### Post by sin1984 on 2006-10-21
should i just make all the mount points in partion 3, which is the 40gb ext3 partition i made?

---

### Post by Sef on 2006-10-21
> you must mount one partition on the root file system ("/") and you must choose at least one partition for use as swap space.


I would make a swap partition out of a small bit of the the empty space.  Swap should be double that of ram.

Read the [Illustrated Dual Boot]("http://users.bigpond.net.au/hermanzone/") to show you how to dual boot and more.

---

