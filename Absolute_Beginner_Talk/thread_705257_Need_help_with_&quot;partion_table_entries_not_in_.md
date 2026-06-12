---
title: "Need help with &quot;partion table entries not in disk order&quot;"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by chicagojack on 2008-02-23
First off, I am very new to Ubuntu, so please bare with me.
Somewhere along the line I believe I may have messed up either my partition table or my /etc/fstab file and now I am not sure which one to try and fix, the partition table or the /etc/fstab file.

The output of /etc/fstab is as follows:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=c50a5991-1b2f-4f45-b608-f9bafa44eb16 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb1
UUID=1423B94E30A5FB8D /media/sdb1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdc1
UUID=263303467BA53232 /media/sdc1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda1
UUID=3d3ab6fe-72d2-4899-8494-e9ea43d28479 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0


The output of the fdisk -l is as follows:

jack@file-server:~$ cd /
jack@file-server:/$ sudo fdisk -l
[sudo] password for jack:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38913   312568641    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000cab66

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38913   312568641    7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000bf3fe

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1           58979       60801    14643247+  82  Linux swap / Solaris
/dev/sdc2   *           1       58978   473740753+  83  Linux

Partition table entries are not in disk order
jack@file-server:/$ 

Can someone help get my "Partition table entries back in disk order"?
Thanks in advance

---

### Post by monktbd on 2008-02-23
> **chicagojack said:**
> 

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1           58979       60801    14643247+  82  Linux swap / Solaris
/dev/sdc2   *           1       58978   473740753+  83  Linux

Partition table entries are not in disk order
jack@file-server:/$ 

```
Can someone help get my "Partition table entries back in disk order"?
Thanks in advance

Does it cause a problem?
Mine are not in order either and it does not matter for me at all.
It is only an information that the partition labeled with 1 (sdc1 in this case) is not physically the first partition on the harddisk. You can easily see that with the start/end blocks in the fdisk -l output.

if you don't like to see the sdc2 mounted to /media/sdc2 and not having a sdc1 at all visible (because it is swap) you can always mount your sdc2 partition to any place you would like to.

on another note your fstab and fdisk output dont seem to match, sda and sdc seem to be interchanged,
> # /dev/sda1
UUID=3d3ab6fe-72d2-4899-8494-e9ea43d28479 none swap sw 0 0
> /dev/sdc1 58979 60801 14643247+ 82 Linux swap / Solaris
did you copy/paste the output or did you write it by hand?

---

### Post by dstew on 2008-02-23
> Can someone help get my "Partition table entries back in disk order"?That is not really a problem, it just gives that comment. Your real problem is that your fstab entries do not match what your partitions really are. For example, in fstab your /dev/sda1 entry is> # /dev/sda1
UUID=3d3ab6fe-72d2-4899-8494-e9ea43d28479 none swap sw 0 0But in your fdisk output, /dev/sda1 is> /dev/sda1 * 1 38913 312568641 7 HPFS/NTFSThere are other apparent mis-matches.

There are two ways to solve this. One is to replace the UUID numbers in your fstab with the linux device names, as shown in fdisk. It is pretty clear from your fdisk output that your linux installation root file system is now in the /dev/sdc2 partition. So, you need to edit /etc/fstab this way. Change```
# /dev/sda2
UUID=c50a5991-1b2f-4f45-b608-f9bafa44eb16 / ext3 defaults,errors=remount-ro 0 1
```to```
# /dev/sdc2
/dev/sdc2 / ext3 defaults,errors=remount-ro 0 1
```Do the same for the other entries. The root file system must come first in your fstab, otherwise the other file systems won't have any mount points to attach to!

The other way (if you are curious) is to continue to use the UUID numbers. This can help if you are in the habit of putting in new distributions, or moving disks aroung, and you want fstab to stay constant. To figure out which UUID goes with which linux device name, use the command  **sudo vol_id *device***  For example, in my system, I get this for /dev/sda1:```
dad@ubuntu:~$ sudo vol_id /dev/sda1
Password:
ID_FS_USAGE=filesystem
ID_FS_TYPE=ext3
ID_FS_VERSION=1.0
ID_FS_UUID=426945e2-1cd9-4f4a-b1ce-8dd0b07d9e4c
ID_FS_LABEL=
ID_FS_LABEL_SAFE=
dad@ubuntu:~$ 

```Then you can match the UUID to the correct mount commands in fstab.

---

### Post by chicagojack on 2008-02-23
In answer to the question - Iis it causing a problem?
My answer: I do not know.

I will try dstew's recommendation and let you know what happens
Thanks, dstew for the suggestion

---

### Post by Duck2006 on 2008-02-23
This may help with the editing in your fstab

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by chicagojack on 2008-02-23
Hey guys, it looks like I now have a new challenge.
I am attempting to follow dstew's instructions; however I am having trouble savings my changes to the /etc/fstab.

I am using the Text Editor found in the Applications drop down menu; but when I attempt to save I get the following error:
Could not save the file /etc/fstab_backup
You do not have the permissions necessary to save the file. 
Please check that you typed the location correctly and try again.

I assume it must be a "permissions setting"; but I am pretty sure I gave myself /root permissions.
Any ideas on how I can make changes to the /etc/fstab and SAVE them?

---

### Post by chicagojack on 2008-02-23
Thanks to Duck2004 I "discovered" how to use a command line text editor and changed the /etc/fstab; the results are listed below:

jack@file-server:/$ sudo cat /etc/fstab
[sudo] password for jack:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc2
UUID=c50a5991-1b2f-4f45-b608-f9bafa44eb16 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=1423B94E30A5FB8D /media/sdb1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb1
UUID=263303467BA53232 /media/sdc1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdc1
UUID=3d3ab6fe-72d2-4899-8494-e9ea43d28479 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

I then ran the fdisk -l command and received the following output:

jack@file-server:/$ sudo  fdisk-l
sudo: fdisk-l: command not found
jack@file-server:/$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38913   312568641    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000cab66

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38913   312568641    7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000bf3fe

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1           58979       60801    14643247+  82  Linux swap / Solaris
/dev/sdc2   *           1       58978   473740753+  83  Linux

Partition table entries are not in disk order

Note I still have the "Partition table entries are not in disk order" error message; however, I feel better that dtew's instructions got my /etc/fstab more aligned with my partition tables entries. 
But, it still begs the question - do or don't I have a problem?

---

### Post by dstew on 2008-02-23
If your system works, you do not have a problem. Ignore the "Partition table entries are not in disk order" message. The only way to get rid of that message is to re-partition. Having out-of-order partitions has no effect on how your system functions.

---

### Post by chicagojack on 2008-02-23
Thanks dstew.
My system does work; so, I guess I will leave it alone and move on.
I appreciate your help.

---

