---
title: "Having difficulty converting external HD into vfat"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by maddbaron on 2007-02-14
Hello, I recently bought an external harddrive I plugged it in and it mounted itself as ntfs but I cannot write to it or transfer files to it. I was told to use gparted to make it a vfat I opened gparted but there is no option to do that. Am I to unmount it then remount it? or is there another method?

Thanks in advance.

---

### Post by taurus on 2007-02-14
You need to unmount it first before you can format it to vfat.  Otherwise, install ntfs-3g if you want to write to ntfs filesystem.

[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

---

### Post by eternalsword on 2007-02-14
perhaps try unmounting and then opening gparted.  I don't think it will allow repartitioning of mounted partitions.

---

### Post by maddbaron on 2007-02-14
> **taurus said:**
> You need to unmount it first before you can format it to vfat.  Otherwise, install ntfs-3g if you want to write to ntfs filesystem.

[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

When I unmounted it I only had the option to make it ext3 or a linux swap I want to be able to use it on a windows system as well. Do I unmount close gparted then reopen gparted and remount with new options?

---

### Post by maddbaron on 2007-02-14
> **eternalsword said:**
> perhaps try unmounting and then opening gparted.  I don't think it will allow repartitioning of mounted partitions.


I will try it.

---

### Post by maddbaron on 2007-02-14
ok I converted it to fat32 but I am still unable to write to it.
Is there something to do in konsole?

---

### Post by taurus on 2007-02-14
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by maddbaron on 2007-02-14
> sudo fdisk -l
Password:

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         383     3076416   12  Compaq diagnostics
/dev/hda2   *         384        3828    27671962+   c  W95 FAT32 (LBA)
/dev/hda3            3829        3892      514080   82  Linux swap / Solaris
/dev/hda4            3893        7296    27342630   83  Linux

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

[B]   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2       24321   195350400    f  W95 Ext'd (LBA)
/dev/sda5               2       24321   195350368+   b  W95 FAT32[/B]


I have no idea what to do next...its already mounted and converted. I just want to be able to write to it. 
*EDIT*
I can write to it but only if I  sudo konquerer. So my user permissions aren't set. How do I set them?

---

### Post by taurus on 2007-02-14
Did you add an entry in /etc/fstab to mount /dev/sda5?  Can you post your /etc/fstab here?

```
cat /etc/fstab
```

---

