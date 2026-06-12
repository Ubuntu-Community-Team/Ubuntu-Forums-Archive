---
title: "Automatically mount Lacie HD at boot time"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by Keio on 2007-08-31
HI all, this is my first post.

Ok, I have a Lacie mobile drive. When I plug it in it's automatically mounted to /media/LACIE. That's good.
But when I start/boot my laptop with the Lacie HD connected to it it doesn't mount automatically. I have to unplug it and then plug it again.

So, I'd like it to mount automatically when the pc is booted.

Notice that all other usb sticks are mounted automatically at boot time to /media/disk , /media/disk1 , etc.

Here is the fdisk command:

keio@ubuntu:~$ fdisk -l

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19457   156288321    c  W95 FAT32 (LBA)


And the fstab file:

keio@ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=18270eb4-56fb-481b-83a2-9f83f11fdfc2 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=de89a893-24d6-4eaa-a178-8f05cd93e5fc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0



I use Ubuntu feisty fawn. Any help? thanks!

---

### Post by Keio on 2007-08-31
Ok, i know everybody ask this question. but i haven't found the solution and i searched a lot.

Problem is, I want it to be mounted automatically when pc startup Or when i log in, or even if i a just plug it in in the middle of a session. Like any othe usb stick. I don't get why it isn't working.

Please help.

---

