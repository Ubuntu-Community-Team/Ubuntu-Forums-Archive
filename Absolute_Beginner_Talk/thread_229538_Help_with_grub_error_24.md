---
title: "Help with grub error 24"
date: 2006-08-04
forum: Absolute Beginner Talk
---

### Post by gargoyle on 2006-08-04
When I try and start I get the grub error 24.
> 24 : Attempt to access block outside partition
    This error is returned if a linear block address is outside of the disk partition. This generally happens because of a corrupt filesystem on the disk or a bug in the code handling it in GRUB (it's a great debugging tool). 

I have no idea of what this really says.  Could some interpret it for me and point me to possible solution. I have done a search on and came across only one entry. But could not see a solution to the problem.

If this helps here is my harddrives
ubuntu@ubuntu:~$ sudo fdisk /dev/hda -l

Disk /dev/hda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1020     8193118+   b  W95 FAT32
/dev/hda2            1021        2434    11357955    f  W95 Ext'd (LBA)
/dev/hda5            1021        2434    11357923+   b  W95 FAT32
ubuntu@ubuntu:~$ sudo fdisk /dev/hdb -l

Disk /dev/hdb: 40.9 GB, 40982151168 bytes
255 heads, 63 sectors/track, 4982 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        1275    10241406    c  W95 FAT32 (LBA)
/dev/hdb2            1276        3877    20900565    f  W95 Ext'd (LBA)
/dev/hdb3   *        3878        4982     8875912+  83  Linux
/dev/hdb5            1276        2550    10241406    b  W95 FAT32
/dev/hdb6            2551        3825    10241406    b  W95 FAT32
/dev/hdb7            3826        3877      417658+  82  Linux swap / Solaris
ubuntu@ubuntu:~$

As you can see 2 hard drives C:winxp and second harddrive holding Ubuntu.
I have also reseated all of the connectors to the harddrive both data and power, still get the same resutls.
So other then a reinstall where do I go from here?

---

### Post by patrick295767 on 2006-08-04
> **gargoyle said:**
> When I try and start I get the grub error 24.


I have no idea of what this really says.  Could some interpret it for me and point me to possible solution. I have done a search on and came across only one entry. But could not see a solution to the problem.

If this helps here is my harddrives
ubuntu@ubuntu:~$ sudo fdisk /dev/hda -l

Disk /dev/hda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1020     8193118+   b  W95 FAT32
/dev/hda2            1021        2434    11357955    f  W95 Ext'd (LBA)
/dev/hda5            1021        2434    11357923+   b  W95 FAT32
ubuntu@ubuntu:~$ sudo fdisk /dev/hdb -l

Disk /dev/hdb: 40.9 GB, 40982151168 bytes
255 heads, 63 sectors/track, 4982 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        1275    10241406    c  W95 FAT32 (LBA)
/dev/hdb2            1276        3877    20900565    f  W95 Ext'd (LBA)
/dev/hdb3   *        3878        4982     8875912+  83  Linux
/dev/hdb5            1276        2550    10241406    b  W95 FAT32
/dev/hdb6            2551        3825    10241406    b  W95 FAT32
/dev/hdb7            3826        3877      417658+  82  Linux swap / Solaris
ubuntu@ubuntu:~$

As you can see 2 hard drives C:winxp and second harddrive holding Ubuntu.
I have also reseated all of the connectors to the harddrive both data and power, still get the same resutls.
So other then a reinstall where do I go from here?

hmm not easy
you might check the filesystems of ur disk with live cd
1/ mount your partition /dev/hda
2/ ```
e2fsck --help
```

---

### Post by r4ik on 2006-08-04
Misread your post, sorry

---

