---
title: "Mounting internal hard drive."
date: 2005-12-26
forum: Absolute Beginner Talk
---

### Post by saldie on 2005-12-26
Ok, here is my situation, I boot of a sata hard drive, and yeaterday I installed an internal ide drive to back up stuff.
I created two partitions, ext3 and fat32, I know how to mount the fat32 partition at boot and what to enter in the fstab, from the ubuntu faq.
What do i enter in fstab to have the ext3 partition mount at boot, and be able to allow all user to read/write?

Here is my info:

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        5222    41945683+  83  Linux
/dev/hda2            5223        9729    36202477+  83  Linux

Disk /dev/sda: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1044     8385898+  83  Linux
/dev/sda2            1045        1206     1301265   82  Linux swap / Solaris
/dev/sda3            1207        9039    62918572+  83  Linux

/dev/hda1 is ext3 and /dev/hda2 is fat32.
Thanks for any help.

---

### Post by xmastree on 2005-12-26
```
/dev/hda1       your/mount/point      ext3    defaults     0       1
```Should work.

---

### Post by Sutekh on 2005-12-26
What have you got in your fstab now?

So you want
```
/dev/hda1  /<mount-point>  ext3  defaults  0  2
```

Also it looks as though your /dev/hda2 partition is ext3 also.
[QUOTE=saldie]
/dev/hda2 5223 9729 36202477+ **83 Linux**
[/QUOTE]
I would have expected to see a 'W95 FAT32' instead of Linux

---

### Post by saldie on 2005-12-26
This is my fstab now:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda3       /home           ext3    defaults        0       2
/dev/sda2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

Sorry, but what do you guys mean by "your/mount/point" or <mount point> :oops: 

> Also it looks as though your /dev/hda2 partition is ext3 also.
Quote:
Originally Posted by saldie
/dev/hda2 5223 9729 36202477+ 83 Linux
I would have expected to see a 'W95 FAT32' instead of Linux

I noticed that also Sutekh, but it is fat32, partitioned it with gparted.

---

### Post by Sutekh on 2005-12-26
[QUOTE=saldie]This is my fstab now:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda3       /home           ext3    defaults        0       2
/dev/sda2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

Sorry, but what do you guys mean by "your/mount/point" or <mount point> :oops:[/QUOTE]

By that we mean... *Where* do you want the partition to show up on your computer?

Take a look at your /etc/fstab.
```
...
/dev/sda3 /home ext3 defaults 0 2
...
```
This line means that the partition /dev/sda3 is 'mounted' in the folder /home

So what you need to do is create a folder on your filesystem, at which you want the hda1 partition to appear in, say /shared.  
```
mkdir /shared
```
Then in your /etc/fstab
```
/dev/hda1 /shared .....
```
would 'mount' the hda1 partition in the /shared folder.
You can mount the hda1 partition anywhere you like, provided there is a folder for it to go to.

---

### Post by Sutekh on 2005-12-26
[QUOTE=saldie]
I noticed that also Sutekh, but it is fat32, partitioned it with gparted.[/QUOTE]
I'm not familiar with partitioning with GParted, but I guess we'll have to assume it did it right.  Is it still seen as a FAT32 partition if you run GParted again?

---

### Post by saldie on 2005-12-26
> I'm not familiar with partitioning with GParted, but I guess we'll have to assume it did it right. Is it still seen as a FAT32 partition if you run GParted again?

Yes gparted still shows it as a fat32 partion.
Ok thanks Sutekh, everything is mounted and i can access it.
One more thing, how can I make a link to the ext3 partition, named "shared" folder, on my desktop or under the places menu for easier access?
The fat32 partition has an icon on my desktop.

---

### Post by saldie on 2005-12-26
Ok, nevermind, I figured out how to do something by myself for once.
:p

---

### Post by Sutekh on 2005-12-26
No problem, good to see it working!

---

