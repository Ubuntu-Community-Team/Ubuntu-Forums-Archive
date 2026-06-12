---
title: "Is this the reason why I can't install 7.04?"
date: 2007-04-24
forum: Apple PPC Users
---

### Post by burobaaje on 2007-04-24
I posted a thread earlier concerning  problems installing 7.04 because I could partition for it using either the live or alternate cd.  The partitioner only shows me the entire 80 G HD as free.  I have installed 7.04 on my iBook.  But my iMac has many more partitions according to fdisk!

Here is the output from mac-fdisk:

/dev/hda1         Apple_partition map                         Partition Map    (31K)
/dev/hda2         Apple_Driver43 Macintosh                Driver 4.3          (28K)
/dev/hda3         Apple_Driver43 Macintosh                Driver 4.3          (28K)
/dev/hda4         Apple_Driver_ATA Macintosh           unknown            (28K)
/dev/hda5         Apple_Driver_ATA Macintosh           unknown            (28K)
/dev/hda6         Apple_FWDriver Macintosh              unknown            (28K)
/dev/hda7         Apple_Driver_IOKit Macintosh         unknown            (256K)
/dev/hda8         Apple_Patches Patch Partition         unknown            (256K)
/dev/hda9         Apple_HFS OSX				        HFS                    (32 G)
/dev/hda10         Apple_HFS OSX4			       HFS                    (29 G)
/dev/hda11       Apple_Free Space			      Free Space        (13.5 G)


Could it be that the partitioner in both the live and the alternate cannot handle 10 partitions?  Anyone know what all those small system partitions are for?  They don't exist on the same version  OSX on my iBook!

---

### Post by 3rdalbum on 2007-04-25
I don't know about the Live CD partitioner, but I know the alternate can handle more than 10 partitions. I don't know what all those small system partitions are for, but I've got them on my iMac too.

When you say that they don't exist on your iBook, is that according to OS X or Ubuntu?

---

### Post by pxwpxw on 2007-04-25
The small partitions are the Apple Partition Map and Macos9 drivers. There is an option in Macosx Disk Utility Partition  to include Macos9 drivers. I dont know what Ipartition is, but might help to run Disk Utility (macosx) first aid, to deconfuse the install partitioner.

---

### Post by burobaaje on 2007-04-25
> **3rdalbum said:**
> I don't know about the Live CD partitioner, but I know the alternate can handle more than 10 partitions. I don't know what all those small system partitions are for, but I've got them on my iMac too.

When you say that they don't exist on your iBook, is that according to OS X or Ubuntu?


I have tried both the live and the alternate.  Live gives me no way.  Alternate will show some partitions but they are not all there and the ones it shows is not even close.  For example it will show a partition of x number of bytes and then show free space which totals the entire drive.  mac-fdisk shows the actual partitions which I have shown in the first post, which was edited to show one I left out.

OS X and Ubuntu only both agree on the iBooks partitions.  It only had 3, a partition table, OS X partition, and the free space.  None of the driver stuff exist on that system and they are both 10.4.9.

---

### Post by burobaaje on 2007-04-25
> **pxwpxw said:**
> The small partitions are the Apple Partition Map and Macos9 drivers. There is an option in Macosx Disk Utility Partition  to include Macos9 drivers. I dont know what Ipartition is, but might help to run Disk Utility (macosx) first aid, to deconfuse the install partitioner.

iPartition is a program that allows you to re-partition a drive without totally reformatting.  It can shrink partitions to make room for new partitions.  You cannot work on a boot drive.

I have looked at the partitions in Disk Utility first aid and all seems well, but I will look again.

---

