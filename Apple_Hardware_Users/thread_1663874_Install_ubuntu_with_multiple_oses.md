---
title: "Install ubuntu with multiple oses"
date: 2011-01-10
forum: Apple Hardware Users
---

### Post by macyf on 2011-01-10
I am going to try obast's method of installing ubuntu in a separate hard drive.
I have a mac pro 3.1 with Drive 1 (mac os x), Drive 2 (windows 7). drive 3 (spare dedicated to ubuntu), drive 4 (backup for time machine)
My question is:
Should I remove drive 2 and drive 4 when installing ubuntu to drive 3 using obast's method of simplified installation?
macyf

---

### Post by ronnielsen1 on 2011-01-10
> Should I remove drive 2 and drive 4 when installing ubuntu to drive 3 using obast's method of simplified installation?

No, just make sure you're choosing the right hard drive / partition during installation

I'm not familiar with Obast but:
[http://www.comptalks.com/how-to-install-ubuntu-10-10/](http://www.comptalks.com/how-to-install-ubuntu-10-10/)

---

### Post by macyf on 2011-01-10
> **ronnielsen1 said:**
> No, just make sure you're choosing the right hard drive / partition during installation

I'm not familiar with Obast but:
[http://www.comptalks.com/how-to-install-ubuntu-10-10/](http://www.comptalks.com/how-to-install-ubuntu-10-10/)

Do you have any idea what drive 3 would be listed as.
I definitely want to install correctly.
Thanks
macyf

---

### Post by ronnielsen1 on 2011-01-10
Open up a terminal and type in [COLOR=Navy]sudo fdisk -l [/COLOR]and post what it responds with

---

### Post by macyf on 2011-01-10
The terminal showed that drive 3 is listed as:
Linux = /dev/disk 3s2
Swap = /dev/disk 3s3
macyf

---

### Post by ronnielsen1 on 2011-01-10
Those aren't normal names. Is this what fdisk -l says? 

Usually it will be like the following:

> root@laptop2:/home/ron# fdisk -l

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00023893

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7228    58058878+  83  Linux
/dev/hda2            7229        7296      546210    5  Extended
/dev/hda5            7229        7296      546178+  82  Linux swap / Solaris
root@laptop2:/home/ron# 


I have my home in the same partition as root. I have one hard drive hda. The first partition of the first hard drive will be hda1, the second /hda2 etc.

A second hard drive would be hdb. Same rules apply to partitions

Normally a cd rom or writer would be hdc but if you had a 3rd hard drive it would probably take that designation.

> The hard drives are labelled in the following way in Linux and FreeBSD: 
                        Linux           FreeBSD
First IDE drive         /dev/hda        /dev/wd0
Second IDE drive        /dev/hdb        /dev/wd1
First SCSI drive        /dev/sda        /dev/sd0
Second SCSI drive       /dev/sdb        /dev/sd1
The partitions (FreeBSD slices) on an IDE drive are labelled in the following way (/dev/hda is used as an example): 
                                Linux           FreeBSD
First primary partition         /dev/hda1       /dev/wd0s1
Second primary partition        /dev/hda2       /dev/wd0s2
Third primary partition         /dev/hda3       /dev/wd0s3
Fourth primary partition        /dev/hda4       /dev/wd0s4
The partitions in my FreeBSD slice is labelled in the follow
[http://tldp.org/HOWTO/Linux+FreeBSD-2.html](http://tldp.org/HOWTO/Linux+FreeBSD-2.html)


Linux = /dev/disk 3s2
Swap = /dev/disk 3s3

doesn't fit

---

### Post by macyf on 2011-01-11
Last login: Mon Jan 10 19:15:28 on ttys000
Macy-XXXXX-Mac-Pro:~  BigMac$ sudo fdisk -l
Password:
fdisk: illegal option --l
usage: fdisk [-ieu] [-f mbrboot] [-c cyl -h head - s sect] [-S size] [-r] [-a style] disk
     -i: initialize disk with new MBR
     -u: update MBR code, preserve partition table
     -e: edit MBRs on disk interactively
     -f: specify non-standard MBR template
     -chs: specify disk geometry
     -S: specify disk size
     -r: read partition specs from stdin (implies -i)
     -a: auto-partition with the given style
     -d: dump partition table
     -y: don't ask questions
     -t: test if disk is partitioned
'disk' is of the form /dev/rdisk0.
auto-partition styles:
     boothfs     8Bb boot plus HFS+ root partition (default)
     bootufs     8Mb boot plus UFS root partition
     hfs             Entire disk as one HFS+ partition
     ufs             Entire disk as one UFS partition
     dos            Entire disk as one DOS partition
     raid            Entire disk as one 0xAC partition

This is what shows when I command:  sudo fdisk -l(lower case L)

When I command sudo df -h I get this:
File System          Size        Used        Avail     Capacity   Mounted on
/dev/disk0s2      298Gi     18Gi        279Gi        7%         /
devfs                    114Ki     114Ki      114Ki    100%         /dev
/dev/disk3s2      270Gi     405Mi     270Gi         1%         /Volumes/Linux
/dev/disk1s2      298Gi      18Gi       280Gi         6%         /Volumes/Backup
/dev/disk 3s3      27Gi      111Mi       27Gi         1%         /Volumes/Swap
/dev/disk2s2      298Gi        50Gi     248Gi        17%        /Volumes/BOOTCAMP
map -hosts              0Bi          0Bi           0Bi      100%        /net
map auto-home      0Bi          0Bi           0Bi      100%        /home

If you notice   /dev/disk3s2 and /dev/disk3s3 are Linux and Swap respectfully
This is my 3rd hard drive which I partitioned and selected GUID Partition Table
When I ran advanced settings in ubuntu it showed 4 drives which 3 of them are HFS+ and 1 is NTFS(Windows)
I would guess that the first drive /dev/sda would be Mac Os X?
Do you have any ideas on this?
thanks
macyf

---

### Post by macyf on 2011-01-11
Last login: Mon Jan 10 19:15:28 on ttys000
Macy-XXXXX-Mac-Pro:~  BigMac$ sudo fdisk -l
Password:
fdisk: illegal option --l
usage: fdisk [-ieu] [-f mbrboot] [-c cyl -h head - s sect] [-S size] [-r] [-a style] disk
     -i: initialize disk with new MBR
     -u: update MBR code, preserve partition table
     -e: edit MBRs on disk interactively
     -f: specify non-standard MBR template
     -chs: specify disk geometry
     -S: specify disk size
     -r: read partition specs from stdin (implies -i)
     -a: auto-partition with the given style
     -d: dump partition table
     -y: don't ask questions
     -t: test if disk is partitioned
'disk' is of the form /dev/rdisk0.
auto-partition styles:
     boothfs     8Bb boot plus HFS+ root partition (default)
     bootufs     8Mb boot plus UFS root partition
     hfs             Entire disk as one HFS+ partition
     ufs             Entire disk as one UFS partition
     dos            Entire disk as one DOS partition
     raid            Entire disk as one 0xAC partition

This is what shows when I command:  sudo fdisk -l(lower case L)

When I command sudo df -h I get this:
File System          Size        Used        Avail     Capacity   Mounted on
/dev/disk0s2      298Gi     18Gi        279Gi        7%         /
devfs                    114Ki     114Ki      114Ki    100%         /dev
/dev/disk3s2      270Gi     405Mi     270Gi         1%         /Volumes/Linux
/dev/disk1s2      298Gi      18Gi       280Gi         6%         /Volumes/Backup
/dev/disk 3s3      27Gi      111Mi       27Gi         1%         /Volumes/Swap
/dev/disk2s2      298Gi        50Gi     248Gi        17%        /Volumes/BOOTCAMP
map -hosts              0Bi          0Bi           0Bi      100%        /net
map auto-home      0Bi          0Bi           0Bi      100%        /home

If you notice   /dev/disk3s2 and /dev/disk3s3 are Linux and Swap respectfully
This is my 3rd hard drive which I partitioned and selected GUID Partition Table
When I ran advanced settings in ubuntu it showed 4 drives which 3 of them are HFS+ and 1 is NTFS(Windows)
I would guess that the first drive /dev/sda would be Mac Os X?
Do you have any ideas on this?
thanks
macyf

---

### Post by ronnielsen1 on 2011-01-11
> If you notice   /dev/disk3s2 and /dev/disk3s3 are Linux and Swap respectfully
This is my 3rd hard drive which I partitioned and selected GUID Partition Table
When I ran advanced settings in ubuntu it showed 4 drives which 3 of them are HFS+ and 1 is NTFS(Windows)
I would guess that the first drive /dev/sda would be Mac Os X?
Do you have any ideas on this?

I'm sorry. Obviously a mac with linux looks at things differently than a PC with linux. If I had to make a GUESS I would say that /dev/disk3s2vand /dev/disk3s3 are your linux partitions and this is where you need to point the installer. The naming of the hard drives is unfamiliar to me. Hopefully someone with mac experience pipes up

---

### Post by ronnielsen1 on 2011-01-12
[https://help.ubuntu.com/community/MacBook3-1/Mave](https://help.ubuntu.com/community/MacBook3-1/Mave)

[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation#Other](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation#Other) Partitioning Options Multi-bootingrick

See if these pages help you

---

