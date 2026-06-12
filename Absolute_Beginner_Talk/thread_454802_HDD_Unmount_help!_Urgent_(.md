---
title: "HDD Unmount help! Urgent :("
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by Dark Star on 2007-05-25
Hello. 
I am having a partition called sda1 . The problem is I cant cop my file in it after I unmount it copies the file but show a error the pic will show u.. Also after the close the HDD window then if I wil open it again the file present in it dissapear and I need to unmount again.. Plz help me how to permanently unmount it. Also I had 2 partition 1 using music file 1 using my some imp files. These partitions are created in WIndows since I removed Windows now I cannot copy any thing nor I can edit anything present inn it. Help Here is the problem screenshot

[http://img90.imageshack.us/img90/2894/helpqn5.png](http://img90.imageshack.us/img90/2894/helpqn5.png)

---

### Post by drowner on 2007-05-25
could you show me the output of the fstab and mtab?

cat /etc/fstab

cat /etc/mtab

---

### Post by drowner on 2007-05-25
oh, and make that picture smaller! or post a link to it instead please. Its far too big.

---

### Post by Dark Star on 2007-05-25
I did not know what u saying :( ;:@ Plz help me dude I am new to Linux :)

---

### Post by drowner on 2007-05-25
> **Dark Star said:**
> I did not know what u saying :( ;:@ Plz help me dude I am new to Linux :)

Ok

open a terminal window, and type
```

cat /etc/fstab
```

and paste here what it says.

the type
```

cat /etc/mtab
```

and paste here what it says

then type
```

sudo fdisk -l
```

and paste here what it says

---

### Post by Dark Star on 2007-05-25
1 commant output

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=9510f80c-fc7d-42a4-8fb9-ac136823c000 /               ext2    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=94F838BCF8389F04 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=705E-3011  /media/sda5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=48D0DA7CD0DA7024 /media/sda6     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda7
UUID=5ffa4eb9-f991-4683-8f14-ddf850cb05a0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

2'nd command output

/dev/sda3 / ext2 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.20-15-generic/volatile tmpfs rw 0 0
/dev/sda1 /media/sda1 ntfs rw,nls=utf8,umask=007,gid=46 0 0
/dev/sda5 /media/sda5 vfat rw,utf8,umask=007,gid=46 0 0
/dev/sda6 /media/sda6 ntfs rw,nls=utf8,umask=007,gid=46 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0

3'rd command output

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1275    10241406    7  HPFS/NTFS
/dev/sda2            1276        6949    45576405    f  W95 Ext'd (LBA)
/dev/sda3            6950        9728    22322317+  83  Linux
/dev/sda5            1276        3825    20482843+   b  W95 FAT32
/dev/sda6            3826        6757    23551258+   7  HPFS/NTFS
/dev/sda7            6758        6949     1542208+  82  Linux swap / Solaris

---

### Post by drowner on 2007-05-25
You are having a few problems here.


Firstly, Your sda1 is a windows NTFS file system. Linux cannot usually write to NTFS.  see this tutorial: [https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

