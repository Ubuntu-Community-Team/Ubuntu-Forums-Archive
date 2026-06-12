---
title: "Post Install Partition Help"
date: 2006-06-05
forum: Absolute Beginner Talk
---

### Post by cabcard on 2006-06-05
When I partitioned, this is how I wanted my setup.

windows (All remaining ~45GB) --> Ubuntu (15GB) --> Swap (1GB)

The install was a success and I can boot into windows or ubuntu. The problem is my partitioning is actually:

windows (15GB) --> Ubuntu (All remaining ~45GB) --> Swap (1GB)

Is there a way to take space from Ubuntu and put it on the windows partition?
I tried using GParted, but it would not let me add the space to the windows partition, unless of course I am missing something.

Here is the output from my /etc/fstab file. Note that it doesn't show my windows partition, why is this?

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


**Edit** I'm running Dapper 6.06

---

### Post by anaconda on 2006-06-05
I think it is possible to resize the partitions (somehow), but I would install those again... 
Resizing would be complicated, because all ubuntus files will be at the beginning of the ubuntu partition, so those would have to be moved forward to make the beginning of ubuntu empty for windows...

2nd question.
if you installed windows after ubuntu, then windows partition couldn't be on your fstab file if you haven't added it there. (ubuntu doesn't scan the fixed disks when you boot. It only scans if there are any NEW removable drives. ie. USB or SATA, or SCSI disks..)
But dont worry. whatever the reason you can add your windows partition to your fstab-file... 

But if you decide to reinstall everything you should install windows first (it is much more demanding), that way ubuntus installer detects windows, and adds it to your fstab, and boot loader...

---

### Post by cabcard on 2006-06-05
[QUOTE=anaconda]I think it is possible to resize the partitions (somehow), but I would install those again... 
Resizing would be complicated, because all ubuntus files will be at the beginning of the ubuntu partition, so those would have to be moved forward to make the beginning of ubuntu empty for windows...

2nd question.
if you installed windows after ubuntu, then windows partition couldn't be on your fstab file if you haven't added it there. (ubuntu doesn't scan the fixed disks when you boot. It only scans if there are any NEW removable drives. ie. USB or SATA, or SCSI disks..)
But dont worry. whatever the reason you can add your windows partition to your fstab-file... 

But if you decide to reinstall everything you should install windows first (it is much more demanding), that way ubuntus installer detects windows, and adds it to your fstab, and boot loader...[/QUOTE]

I did install windows first.....

And XP does show up in the bootloader and I can successfully boot into it.

---

### Post by bruenig on 2006-06-05
> 
When I partitioned, this is how I wanted my setup.

windows (All remaining ~45GB) --> Ubuntu (15GB) --> Swap (1GB)

The install was a success and I can boot into windows or ubuntu. The problem is my partitioning is actually:

windows (15GB) --> Ubuntu (All remaining ~45GB) --> Swap (1GB)

Is there a way to take space from Ubuntu and put it on the windows partition?
I tried using GParted, but it would not let me add the space to the windows partition, unless of course I am missing something.

I've needed to do something similar before and this is how i did it. Put in the ubuntu install cd, which is a live cd. Go to System>Administration>Gnome Partition Editor. Because you are using the live cd none of the partitions are mounted and therefore can all be modified. When you get into Gparted, resize the ubuntu partition to 15 GB and make sure the extra space that is created by that resize is positioned in front of the Ubuntu partition so that it can be used by windows. Resize the windows partition to take up the extra unpartitioned space that was created by the Ubuntu resize. Apply changes and, take out the live cd and reboot. Everything should be fine.

You might have to install ubuntu again, I don't think so.

And just some advice, I would use some of that extra space, format it as fat32 and use it to store personal files. By doing that you can share files between Ubuntu and windows without having to install some NTFS read write thing for linux or some ext3 driver for windows. (If you do that, you will have to mount it though.)

---

