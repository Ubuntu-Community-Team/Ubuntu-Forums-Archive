---
title: "Grub Error 23"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by Grogs on 2007-05-23
I've just installed Vista, XP and Ubuntu (in that order) on my PC today. They're all on one of 5 drives in my computer (which are all for data). When I try and start my computer I get a message that Grub 1.5 or whatever is loading and then it states there's an error, number 23. (May be 21 but pretty certain 23) I don't know where to go from here, had a quick search of the forums and wiki, with no results, so I'm hoping someone here can explain what this error is an what I can do about it.

---

### Post by dstew on 2007-05-23
This means that the grub boot loader could not find its root directory. Usually this is because of some error in the grub installation, or that the BIOS disk enumeration has changed since grub was first installed. Are your disks and BIOS is the same configuration as they were when Ubuntu was installed? If not, put them back the way they were, and you should be OK. If they are still as they were, you might need to reinstall grub (but not all of Ubuntu).

Boot the Ubuntu live CD and enter the command```
sudo fdisk -l
```in a terminal window, and post the results on the forum. This will show us how your disks are arranged.

---

### Post by Grogs on 2007-05-23
Results, from sudo fdisk -l, are as follows:

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30401   244196001    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    7  HPFS/NTFS

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       12749   102400000    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdc2           12750       38913   210162330    f  W95 Ext'd (LBA)
/dev/sdc5           12750       25497   102398278+   7  HPFS/NTFS
/dev/sdc6           25498       25746     2000061   82  Linux swap / Solaris
/dev/sdc7           25747       38913   105763896   83  Linux

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       60801   488384001    7  HPFS/NTFS

Disk /dev/sde: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1       24792   199141708+   7  HPFS/NTFS

Disk /dev/sdf: 4119 MB, 4119683584 bytes
127 heads, 62 sectors/track, 1021 cylinders
Units = cylinders of 7874 * 512 = 4031488 bytes

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   ?      237462      258886    84344761   69  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(68, 13, 10) logical=(237461, 55, 42)
Partition 1 has different physical/logical endings:
     phys=(288, 115, 43) logical=(258885, 6, 25)
Partition 1 does not end on cylinder boundary.
/dev/sdf2   ?      216094      453569   934940732+  73  Unknown
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(371, 114, 37) logical=(216093, 51, 38)
Partition 2 has different physical/logical endings:
     phys=(366, 32, 33) logical=(453568, 105, 4)
Partition 2 does not end on cylinder boundary.
/dev/sdf3   ?           1           1           0   74  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(371, 114, 37) logical=(0, 41, 32)
Partition 3 has different physical/logical endings:
     phys=(372, 97, 50) logical=(0, 41, 31)
Partition 3 does not end on cylinder boundary.
/dev/sdf4          366483      366489       26207+   0  Empty
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(0, 0, 0) logical=(366482, 30, 25)
Partition 4 has different physical/logical endings:
     phys=(0, 0, 0) logical=(366488, 113, 49)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

```

Thanks for your help. :)

---

### Post by dstew on 2007-05-23
OK, it looks like /dev/sdc7 is your Linux partition, and should contain the grub root files. We need to make sure that grub can see this partition. From your Live CD terminal, enter the command **grub**. This will get us a grub command line, indicated by the **grub>** prompt. At the grub> prompt, you can enter various commands that grub will execute. Try grub>help to see a list. For now, let's get grub to look for its usual root directory. Enter ```
grub>find /boot/grub/menu.lst
```Post the output. It seems like it should find the file, and give the partition as (hd2,6).

---

### Post by Grogs on 2007-05-23
> **dstew said:**
> OK, it looks like /dev/sdc7 is your Linux partition, and should contain the grub root files. We need to make sure that grub can see this partition. From your Live CD terminal, enter the command **grub**. This will get us a grub command line, indicated by the **grub>** prompt. At the grub> prompt, you can enter various commands that grub will execute. Try grub>help to see a list. For now, let's get grub to look for its usual root directory. Enter ```
grub>find /boot/grub/menu.lst
```Post the output. It seems like it should find the file, and give the partition as (hd2,6).

It gives the following output:
```
Error 15: File not found

```
I guess that's a bit of a problem... :p

---

### Post by Grogs on 2007-05-24
Anyone have any ideas what I should do next? I just checked and it was actually error **21** *not 23*. How can I reinstall GRUB or create this menu.lst?

---

### Post by dstew on 2007-05-24
This is a problem usually related to your BIOS. Grub depends on your BIOS recognizing disks. Sometimes, the BIOS you have will only detect some of your disks, but when you boot an operating system, the more powerful software in the OS will see all of your disks. Clearly, the Live CD OS can see all your disks, but that is not good enough to get grub to work.

If you have BIOS skills, you can see if there are any settings that you can change to help grub to see the disk named /dev/sdc.

One sure way to get grub to work is to re-install Linux, but create a small (100 Mb) partition at the beginning of /dev/sda, and give it the mount point of /boot. The rest of Linux can be installed in /dev/sda7 as you have already done. But to do this, you would have to shrink the NTFS partition on /dev/sda to make room for the boot partition, and you might end up with problems booting your Windows system. These problems can be overcome, but can be anxiety-provoking.

Perhaps you can put the /boot partition on /dev/sdb. This would only work if grub can see the disk. One way to test if grub can see a disk is to boot the Live CD, run grub from a terminal, and enter at the grub> prompt the command```
grub> geometry (hd1)
```This will return information that grub has obtained from the BIOS regarding that particular disk. Try this command with (hd0), (hd1), etc. to see which of your disks grub can see. Once we know which disks are visible to grub, we can talk about installing a /boot partition on that particular disk.

By the way, the /boot/grub/menu.lst file is on your /dev/sda7 partition, but since that disk is invisible to grub, it could not find it. You will not have to create the file, it is put into the Linux file system by the installer. If you create a /boot partition, it will end up there.

---

