---
title: "Linux - Ntfs mount problems"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by anigodin on 2007-05-01
Hello people,

I have a pentuim 4 1.8 computer with 3 hard drives:
40 GB that has a windows xp installed on it (with two partitions of 15 GB and 25 GB)
60 GB which I use as a media storage disk (with two partitions of 51 GB and 9 GB)
10 GB that I installed Linux Ubuntu 7.04 a few days ago.

Both OS work fine with the dual boot but I have a problem I dont know how to solve. I can mount the XP HD's on the linux and read from them but I cant write to them.
I run the  "sudo apt-get install ntfs-config" command in order to allow linux to write on the XP disks but it's not working.
I asked a friend about this and he told me to run "nano /etc/fstab" command. the reasult I get it this:
[COLOR="Red"]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc1
UUID=2bdb93f7-eda0-4afd-8deb-dd097275858b /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdc5
UUID=7b362686-1728-4bb8-9a95-c46c442adb4c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

My friend told me I need to see the NTFS disk in the list but it's not there.

Any help in solving this problem will be blessed
Thanks in advance

---

### Post by AndrewNi on 2007-05-01
I've heard of it only working for one disk, but not none. I think the problem might be that the partitions aren't automatically mounted on boot. The /etc/fstab file is meant to list file systems that are, and if there is no entry in there for it then perhaps the tool doesn't know what to do, or thinks that there are no NTFS partitions to enable write support for.

---

### Post by dstew on 2007-05-01
Fstab is a "file system table" that contains the instructions used to mount the various file systems when Linux boots up. It is **not** a list of all the file systems that are potentially mountable. To list all the file systems that are available to be mounted, use the command **sudo fdisk -l**.

When we see which filesystem that you want to mount, we can add it to your fstab file. Then, it will mount when Linux boots up.

---

