---
title: "mount partitions at boot"
date: 2006-10-20
forum: Absolute Beginner Talk
---

### Post by mendingo84 on 2006-10-20
i want my partitions to be mounted at boot. how do i do that?

---

### Post by jorn on 2006-10-20
mswindows partitions?

---

### Post by mendingo84 on 2006-10-20
no. fat32 partitions

---

### Post by dannyboy79 on 2006-10-20
we just need to add a certain line to your fstab file which is located in /etc/. please post output  of sudo fdisk -l and tell me out of the results which drive is the fat32 one. or is this a drive that's on the network and not on you local machine?

---

### Post by jorn on 2006-10-20
Try this guide:
[http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite)
If there is something you don't understand, please post.

---

### Post by Aberrix on 2006-10-20
```
cp /etc/fstab /etc/fstab.bak
```

then

```
sudo vi /etc/fstab
```

and add in the appropriate line.

---

### Post by mendingo84 on 2006-10-20
> Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1275    10241406    7  HPFS/NTFS
/dev/sda2            1276       19456   146038882+   f  W95 Ext'd (LBA)
/dev/sda5            1276        3825    20482843+  83  Linux
/dev/sda6            3826       11474    61440561    b  W95 FAT32
/dev/sda7           11475       19456    64115383+   b  W95 FAT32

this is the output of sudo fdisk -l . the partitions that i want to operate on are sda7 and sda6

---

### Post by aysiu on 2006-10-20
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by dannyboy79 on 2006-10-20
> **mendingo84 said:**
> this is the output of sudo fdisk -l . the partitions that i want to operate on are sda7 and sda6

/dev/sda7 /media/fat32-1 vfat rw,uid=1000,gid=1000,iocharset=utf8,umask=0000 0 0

/dev/sda6 /media/fat32-2 vfat rw,uid=1000,gid=1000,iocharset=utf8,umask=0000 0 0

you just need to create the mount point, or wherever you want the hard drives to be mounted to. my example uses /media/fat32-1 and /media/fat32-2.
don't forget to chown the directories cause if not I think they are owned by root
sudo chown usernamehere /media/fat32-1
etc, etc

oh, one other thing, people have been having trouble getting sata drives to be mounted automatically upon boot, it's because the drivers or modules are getting loading after the mountall command, if these are sata drives, do a search in the ubuntu forum, automount sata, and you'll find that you need to add some modules to your /etc/modules file. I think. that's the way I got mine to work.

---

