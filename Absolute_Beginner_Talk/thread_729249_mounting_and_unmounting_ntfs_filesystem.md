---
title: "mounting and unmounting ntfs filesystem"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by zerobinary on 2008-03-19
I have trouble mounting ntfs external hdd and trouble with unmounting ntfs filesystem .
I am using ntfs coniguration tool.
[IMG]http://i183.photobucket.com/albums/x196/zerobinary/Screenshot-1-10.png[/IMG]
[IMG]http://i183.photobucket.com/albums/x196/zerobinary/Screenshot-24.png[/IMG]

---

### Post by ajmorris on 2008-03-19
the easiest, and arguably the best way to do this is with ntfs-3g

so you can ```
sudo apt-get install ntfs-3g
```

then, you can add a line to /etc/fstab to make it automatic if you wish.

---

### Post by glennric on 2008-03-19
Even with ntfs-3g you won't be able to mount the volume.  The best thing for you to do is read that error and do what it says.  Basically you need to boot to windows and check the partition there.  It is possible to do this from linux, but the safest and most reliable way is to boot to windows.

---

### Post by ajmorris on 2008-03-19
> **glennric said:**
> Even with ntfs-3g you won't be able to mount the volume.  The best thing for you to do is read that error and do what it says.  Basically you need to boot to windows and check the partition there.  It is possible to do this from linux, but the safest and most reliable way is to boot to windows.

what error?

**EDIT: **OHHH lol, sorry, the images took a while to load on my slow connection :P

---

### Post by zerobinary on 2008-03-19
aliceminer@aliceminer:~$ sudo mount -t ntfs-3g /dev/sdb 1/media/1942 -o force
NTFS signature is missing.
Failed to mount '/dev/sdb': Invalid argument
The device '/dev/sdb' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
and how do i unmount the ntfs volume

---

### Post by jan quark on 2008-03-19
have you tried to boot into windows ( if you still have it installed on the machine) and safely remove the external driver?

can you please post the results of these terminal commands

```
mount

sudo fdisk -l
```

---

### Post by zerobinary on 2008-03-20
Thx now is working again. However, when I boot back into window xp and my external hdd has some weird file that i can't delete.
And is there any way to become root using nautilius script so i can unmount the ntfs hdd without having to type all those crazy cmd.

[IMG]http://i183.photobucket.com/albums/x196/zerobinary/untitled-24.jpg[/IMG]
[IMG]http://i183.photobucket.com/albums/x196/zerobinary/untitled1-9.jpg[/IMG]

---

### Post by zerobinary on 2008-03-21
not working again
```

/dev/sdb1               1       60801   488384001    7  HPFS/NTFS
root@aliceminer:~# sudo fdisk -l /dev/sdb1

Disk /dev/sdb1: 500.1 GB, 500105217024 bytes
255 heads, 63 sectors/track, 60800 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69205244

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/sdb1p1   ?       13578      119522   850995205   72  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sdb1p2   ?       45382       79243   271987362   74  Unknown
Partition 2 does not end on cylinder boundary.
/dev/sdb1p3   ?       10499       10499           0   65  Novell Netware 386
Partition 3 does not end on cylinder boundary.
/dev/sdb1p4          167628      167631       25817+   0  Empty
Partition 4 does not end on cylinder boundary.

```

---

