---
title: "Can't read or write freshly formatted ext3 partitions!?"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by 3ntity on 2007-03-09
Hello,
I just formatted and installed Ubuntu 6.06. For some reason, i cannot write to any of my freshly formatted ext3 partitions [see attached screenshot]. It's the case on both my IDE and SATA HDD's. Commands such as 'sudo cp source ext3partition' DO work, but it's annoying to have to work like this, being so used to drag&drop, ... Unmounting and remounting the drives isn't helping either. What can i do?

Anyways, i've attached the results of some commands, hopefully these are of some use, otherwise, just ignore 'em :)

```
****@****-ubuntu:~$ mount
/dev/hdb4 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-23-386/volatile type tmpfs (rw)
/dev/sda3 on /media/Data_2 type ext3 (rw)
/dev/hdb2 on /media/Data_FAT32 type vfat (rw,utf8,umask=007,gid=46)
/dev/hdb6 on /media/Ubuntu_data type ext3 (rw)
/dev/sda1 on /media/Windows type ntfs (rw,nls=utf8,umask=007,gid=46)
/dev/sda2 on /media/Data_1 type ext3 (rw)

```

```
****@****-ubuntu:~$ sudo fdisk -l
Password:

Disk /dev/hdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        3569    28667961    5  Extended
/dev/hdb2   *        3570       22791   154400715    c  W95 FAT32 (LBA)
/dev/hdb3           22792       22864      586372+  82  Linux swap / Solaris
/dev/hdb4           22865       24321    11703352+  83  Linux
/dev/hdb5            3421        3569     1196811   82  Linux swap / Solaris
/dev/hdb6               1        3420    27471055+  83  Linux

Partition table entries are not in disk order

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3187    25599546    7  HPFS/NTFS
/dev/sda2            3188       16241   104856255   83  Linux
/dev/sda3           16242       30514   114647872+  83  Linux
/dev/sda4           30515       30515        8032+   f  W95 Ext'd (LBA)
```

Thanks in advance for any help :)

---

### Post by endtroducing on 2007-03-09
Can you paste your /etc/fstab

E

---

### Post by 3ntity on 2007-03-09
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb4       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda2       /media/Data_1   ext3    defaults        0       2
/dev/sda3       /media/Data_2   ext3    defaults        0       2
/dev/hdb2       /media/Data_FAT32 vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hdb6       /media/Ubuntu_data ext3    defaults        0       2
/dev/sda1       /media/Windows  ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

---

### Post by taurus on 2007-03-09
You just have to change the ownership of /media/Data_1 from root to your login name.  Then, you can write to it whenever you want to.  

Assuming your login name is **john**, do

```
sudo chown -R **john**:**john** /media/Data_1
```

---

### Post by 3ntity on 2007-03-09
> **taurus said:**
> You just have to change the ownership of /media/Data_1 from root to your login name.  Then, you can write to it whenever you want to.  

Assuming your login name is **john**, do

```
sudo chown -R **john**:**john** /media/Data_1
```

Hmm... strange. This command worked for 2 of 3 ext3 partitions [Data_2 and Data_Ubuntu, see previous posts], but not for Data_1. I formatted Data_1 (from ext3) to ext3 after i'd installed dapper, the other ones were formatted with GParted during installation. Any further suggestions?

Thanks a lot already, i now have 100+GB readily available which wasn't so before :D

**EDIT:** I unmounted the partition, then did 'sudo chown -R john:john /dev/sda2', then remounted it and did  'sudo chown -R john:john /dev/sda2', after which it worked :D 

So now it's fully sorted... Thanks!

---

### Post by taurus on 2007-03-09
Reboot and see if you still can write to those two ext3 partitions.

---

### Post by 3ntity on 2007-03-09
> **taurus said:**
> Reboot and see if you still can write to those two ext3 partitions.

:) yepyep, still working :)

Thanks!

---

