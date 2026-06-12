---
title: "Partition Mounting/Partition Permissions"
date: 2006-11-13
forum: Absolute Beginner Talk
---

### Post by iamthekiller on 2006-11-13
I have been using Ubuntu with the KDE desktop environment dual booted with Windows XP for a few days now and I keep stumbling on to the same problem.

Randomly (I'm not sure if it's really random, but I haven't figured out what I could possibly be doing to cause it, so I noted it as random) one of my partitions (labeled /dev/hda10 aka my music partition) unmounts, and it it's place my storage partition (dev/hdb5) takes its place in /media/hda10 as well as /media/hdb5

I've successfully unmounted hdb5 and remounted both partitions to where they should be, but I can't get access to either of them after that. I've been able to access them when they've already mounted the right way at startup, but it seems this issue triggers some sort of permissions issue.

I've tried changing permissions and tinkering with fstab, but nothing seems to be working.

I've also tried creating new directories to mount the partitions into such as /media/music and /media/storage but I run into the same problem of being unable to access them due to permissions.

Here is my fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda11
UUID=2a9c0683-2fb1-4acf-919e-2d48a26f6ab1 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=4C50B7DD50B7CC48 /media/hda1     ntfs    defaults,utf8,umask=007,gid=046   0       1
# /dev/hda10
UUID=72FCD7ACC2C3C541 /media/hda10    ntfs    defaults,utf8,umask=007,gid=046   0       1
# /dev/hda5
UUID=F2346D6B346D342F /media/hda5     ntfs    defaults,utf8,umask=007,gid=046   0       1
# /dev/hda6
UUID=E8D4794ED4791FCC /media/hda6     ntfs    defaults,utf8,umask=007,gid=046   0       1
# /dev/hda7
UUID=1C7480E77480C54C /media/hda7     ntfs    defaults,utf8,umask=007,gid=046   0       1
# /dev/hda8
UUID=AAF45A68F45A3733 /media/hda8     ntfs    defaults,utf8,umask=007,gid=046   0       1
# /dev/hda9
UUID=E0F482F2F482CA6C /media/hda9     ntfs    defaults,utf8,umask=007,gid=046   0       1
# /dev/hdb5
UUID=72FCD7ACC2C3C541 /media/hdb5     ntfs    defaults,utf8,umask=007,gid=046   0       1
# /dev/hda12
UUID=885a2d83-6d81-45d3-b7cc-e38fdded28be none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
```

All partitions are NTFS, but I don't have trouble accessing any of them other than these two when they don't mount right.

If you need any other information, please ask...I could really use the help as I'm very interested in  becoming a full fledged Ubuntu user.

---

### Post by PPAAUULL on 2006-11-13
have you tried ```
sudo mount /media/blah /mnt/
``` I think that should get it done for you. If I am wrong it would be great if someone could correct the code for me. It has been a long time since I used it.

---

