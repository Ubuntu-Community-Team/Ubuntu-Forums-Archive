---
title: "USB flash drive issue"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by mjwhitfield on 2007-06-22
Hi guys, I was wondering if you chould help.  I have a 1GB USB flasg drive that I formatted on a XP machine as FAT32, when I put it in either my Ubuntu or Gentoo machines I get the following Information from fdisk -l

```
Disk /dev/sdb: 1048 MB, 1048576000 bytes
33 heads, 61 sectors/track, 1017 cylinders
Units = cylinders of 2013 * 512 = 1030656 bytes

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?      386556      953625   570754815+  72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(357, 116, 40) logical=(386555, 11, 23)
Partition 1 has different physical/logical endings:
     phys=(357, 32, 45) logical=(953624, 6, 61)
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?       83801     1045563   968014120   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 115, 43) logical=(83800, 2, 1)
Partition 2 has different physical/logical endings:
     phys=(367, 114, 50) logical=(1045562, 23, 53)
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?      928903     1890666   968014096   79  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(366, 32, 33) logical=(928902, 28, 32)
Partition 3 has different physical/logical endings:
     phys=(357, 32, 43) logical=(1890665, 16, 36)
Partition 3 does not end on cylinder boundary.
/dev/sdb4   ?     1433523     1433551       27749+   d  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(372, 97, 50) logical=(1433522, 22, 25)
Partition 4 has different physical/logical endings:
     phys=(0, 10, 0) logical=(1433550, 8, 13)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order
```

Also, not sure if it's important but I also get this info from lsusb

```
Bus 001 Device 011: ID 0ea0:2168 Ours Technology, Inc. Transcend JetFlash 2.0 / Astone USB Drive
```

The drive works fine when mounted, but I'm a little worried about what the errors mean?

Any advice?

---

### Post by Inxsible on 2007-06-22
Its not recognizing your filesystem. I don't know what 72 stands for, but 83 is for Linux, 82 for Swap, 7 for NTFS and so on.

Have you tried re-formatting it ?

---

### Post by mjwhitfield on 2007-06-22
I'm in work at the moment, so I only have my Gentoo machine available to me.  I've formatted it on a Windows machine In the office, and it stays the same.

I've tried to format it using the following but got an error:
```
matthew6600 ~ # mkfs -t vfat /mnt/usb/
mkfs.vfat: No such file or directory
```

I'm assuming I forgot to compile something into my gentoo install.  it's weird that I can mount and use the drive, but it's showing the ideas.

any help much appreciated!

---

### Post by Inxsible on 2007-06-22
> **mjwhitfield said:**
> I'm in work at the moment, so I only have my Gentoo machine available to me.  I've formatted it on a Windows machine In the office, and it stays the same.

I've tried to format it using the following but got an error:
```
matthew6600 ~ # mkfs -t vfat /mnt/usb/
mkfs.vfat: No such file or directory
```

I'm assuming I forgot to compile something into my gentoo install.  it's weird that I can mount and use the drive, but it's showing the ideas.

any help much appreciated!

you are trying to format the mount point instead of the drive. your drive would be something like /dev/sda1

---

### Post by LaRoza on 2007-06-22
If you have the XP machine, run "chkdsk x: /F" replace x with the drive letter.

If you have GParted, I would reformat it, this isn't a "U3" drive by any chance?

---

### Post by mjwhitfield on 2007-06-22
> **Inxsible said:**
> you are trying to format the mount point instead of the drive. your drive would be something like /dev/sda1I get the same error:```
mkfs.vfat: No such file or directory
```> If you have the XP machine, run "chkdsk x: /F" replace x with the drive letter.

If you have GParted, I would reformat it, this isn't a "U3" drive by any chance?It's not a U3 device. 

XP checkdisk is returning no errors.

I don't have GParted, Gentoo wants to emerge about 20 packages to get it going and I can't do that right now, but I'll give it a go on my ubuntu machine at home.  Why is it refering to them as sdb1 sdb2 sdb3 etc? it's not partitioned and it's blank.

anyone have any other suggestions that I can try while at work?

---

### Post by rhmeyer50 on 2007-06-22
Good Day,
My first post here. I went through a similar issue in transferring my FireFox book marks from my Windows FF to Linux FF. I went around and around with getting the Lexar thumb drive mounted. I could see the icon for the bookmarks but when I went to import them nothing happened. Finally, In Windows I scan disked and defragmented the thumb drive. The bookmarks disappeared; meaning, I suppose, they had become corrupted. Since I had inserted and removed the thing so many times its my guess. Anyhow, I picked up the bookmarks again and this time was able to import them with no problem. 
Best,
Rob

---

