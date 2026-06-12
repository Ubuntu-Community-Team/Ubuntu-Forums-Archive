---
title: "Initial partitioning approach"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by pieniaszek on 2007-10-07
Dell Dimension 4550 with XP installed on primary (250GB) and Ubuntu Fiesty on the slave (60GB).
Unable to understand how to use GParted, and do not understand the goals of partitioning, so installed Acronis Disk Director and  used Parttion Expert.  I did search as many sites as I could find to guide in in partition and files types.

This is what I have and I would appreciate any comments so I could make the partitions more efficient.
/dev/sdb1-52.40 GB, /dev/sdb6-15.11 GB, /dev/sdb7-25.14, /dev/sdb10-30.55 GB
The 'Partition',"Filesystem','Mountpoint','Size','Used','Unused', and 'Flags' for each partion are;
/dev/sdb1	ext3	/	52.40 GiB	3.23 GiB	49.17 GiB	boot
/dev/sdb2	extended		94.64 GiB	…	…	lba
/dev/sdb5	linux-swap		4.34 GiB	…	…	
/dev/sdb6	fat32	/media/home	15.11 Gib	15.12 MiB	15.09 GiB	
/dev/sdb7	ntfs	/media/tmp	25.14 GiB	65.22 MiB	25.08 GiB	
/dev/sdb8	ntfs	/media/usr	10.79 GiB	58.00 MiB	10.73 GiB	
/dev/sdb9	fat32	/media/var	10.72 GiB	10.73 MiB	10.71 GiB	
/dev/sdb10	fat32	/media/data	30.55 GiB	15.31 MiB	30.53 GiB

---

### Post by jnorthr on 2007-10-07
opinions differ as to the 'best' approach. Some people choose to dump everything into one single big partition, the root / 
some choose a separate partition for root and another for /home as your preferences live there - so when you move to a newer version you can keep all those options and choices without the need to rebuild a system from scratch.

Read this: [https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

or look here for tips: [http://screencasts.ubuntu.com/Installing_Ubuntu_with_Windows_Dual-Boot](http://screencasts.ubuntu.com/Installing_Ubuntu_with_Windows_Dual-Boot)

and an older guide but perhaps useful : [http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

---

### Post by jpkotta on 2007-10-07
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

