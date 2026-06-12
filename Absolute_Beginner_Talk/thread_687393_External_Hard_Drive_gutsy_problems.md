---
title: "External Hard Drive gutsy problems"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by andybleaden on 2008-02-04
Since upgrading to Gutsy I have been having trouble getting my 2 external HDDs to mount automatically and be accessible. 

They always used to be on my desktop on feisty but I have to go into the system settings section and enable them everytime....then sometimes it does it automatically ...is there a commnad line I can run which will show my problem here?

Andy

---

### Post by jan quark on 2008-02-04
well as a start run and post te results please

```
mount 
```
```

sudo fdisk -l
```

---

### Post by andybleaden on 2008-02-04
Will do as soon as I get home and post the results 

thanks for the quick response

---

### Post by andybleaden on 2008-02-04
Mount gave this 

andy@andy-desktop:~$ mount
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
/dev/hda3 on /home type ext3 (rw)
/dev/hdb1 on /media/hdb1 type ext3 (rw)
securityfs on /sys/kernel/security type securityfs (rw)
andy@andy-desktop:~$


sudo f disk gave this


Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6f1e8855

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1567    12586896   83  Linux
/dev/hda2            1568        1828     2096482+  82  Linux swap / Solaris
/dev/hda3            1829        4865    24394702+  83  Linux

Disk /dev/hdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9007872d

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       24321   195358401   83  Linux

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f9c798a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       38913   312568641    c  W95 FAT32 (LBA)


Clear as mud to me!:confused:

---

### Post by andybleaden on 2008-02-05
bump?

Any ideas anyone?

---

### Post by jan quark on 2008-02-05
```

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6f1e8855

Device Boot Start End Blocks Id System
/dev/hda1 * 1 1567 12586896 83 Linux
/dev/hda2 1568 1828 2096482+ 82 Linux swap / Solaris
/dev/hda3 1829 4865 24394702+ 83 Linux
```

this is your harddrive with you r linux installation

```
Disk /dev/hdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9007872d

Device Boot Start End Blocks Id System
/dev/hdb1 1 24321 195358401 83 Linux
```

this is also a linux partition

```
[COLOR="SandyBrown"]Disk /dev/sda:[/COLOR] 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f9c798a

Device Boot Start End Blocks Id System
[COLOR="SandyBrown"]/dev/sda1 1 38913 312568641 c W95 FAT32 [/COLOR](LBA)
```

this seems to be your external drive formated in the fat 32

pls post the result of 
```

ls /media
```

to have a look if it is already mounted or weh do have to create a mount point first and mount it manually

---

### Post by andybleaden on 2008-02-06
Thanks again for coming back to me on this. I am working at home later today and all tomorrow and so will run this command. 

I have only got one external hard drive plugged in at the moment ( one is a back up) but if you want I can plug that in (it is a 500gb)however I will not do so if you think it will add to the confusion.

Will post results later

---

### Post by andybleaden on 2008-02-07
Results from running mount -l


/dev/hda1 on / type ext3 (rw,errors=remount-ro) []
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
/dev/hda3 on /home type ext3 (rw) []
/dev/hdb1 on /media/hdb1 type ext3 (rw) []
/dev/sda1 on /media/sda1 type vfat (rw,noexec,nosuid,nodev) [Elements]
/dev/sda1 on /media/sda2 type vfat (rw,noexec,nosuid,nodev) [Elements]
securityfs on /sys/kernel/security type securityfs (rw)
/dev/sdc1 on /media/disk type vfat (rw,nosuid,nodev,noatime,flush,uid=1000,utf8,shortname=lower) []


Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6f1e8855

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1567    12586896   83  Linux
/dev/hda2            1568        1828     2096482+  82  Linux swap / Solaris
/dev/hda3            1829        4865    24394702+  83  Linux

Disk /dev/hdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9007872d

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       24321   195358401   83  Linux

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8d399bc0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60800   488375968+   c  W95 FAT32 (LBA)

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f9c798a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    c  W95 FAT32 (LBA)

Disk /dev/sdd: 2043 MB, 2043002880 bytes
255 heads, 16 sectors/track, 978 cylinders
Units = cylinders of 4080 * 512 = 2088960 bytes
Disk identifier: 0x8f752df0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1         978     1995104    c  W95 FAT32 (LBA)

Disk /dev/sdc: 4126 MB, 4126146560 bytes
16 heads, 32 sectors/track, 15740 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       15740     4029424    b  W95 FAT32
andy@andy-desktop:~$

---

### Post by andybleaden on 2008-02-10
pls post the result of 
```

ls /media
```

to have a look if it is already mounted or weh do have to create a mount point first and mount it manually[/QUOTE]

andy@andy-desktop:~$ ls /media
cdrom  cdrom0  cdrom1  floppy  floppy0  hdb1  sda1  sda2

---

### Post by andybleaden on 2008-02-11
I am am not clear about this at all. For an update I have now attached both external HD at sda1 and sda2 but they do not always mount automatically and one of them is logged as root and not as me which I am not sure how to change. I tried the chown command thing but it ain't for changing. So as you will see on the posting below I have two hdds one as andy and one as root...the root one 500GB I cannot write to at the moment so I need to be able to change its ownership


Any ideas??


/dev/hda1 on / type ext3 (rw,errors=remount-ro) []
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
/dev/hda3 on /home type ext3 (rw) []
/dev/hdb1 on /media/hdb1 type ext3 (rw) []
/dev/sda1 on /media/sda1 type vfat (rw,noexec,nosuid,nodev) [Elements]
/dev/sda1 on /media/sda2 type vfat (rw,noexec,nosuid,nodev) [Elements]
securityfs on /sys/kernel/security type securityfs (rw)
/dev/sdc1 on /media/disk type vfat (rw,nosuid,nodev,noatime,flush,uid=1000,utf8,short name=lower) []


Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6f1e8855

Device Boot Start End Blocks Id System
/dev/hda1 * 1 1567 12586896 83 Linux
/dev/hda2 1568 1828 2096482+ 82 Linux swap / Solaris
/dev/hda3 1829 4865 24394702+ 83 Linux

Disk /dev/hdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9007872d

Device Boot Start End Blocks Id System
/dev/hdb1 1 24321 195358401 83 Linux

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8d399bc0

Device Boot Start End Blocks Id System
/dev/sda1 1 60800 488375968+ c W95 FAT32 (LBA)

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f9c798a

Device Boot Start End Blocks Id System

---

### Post by andybleaden on 2008-02-12
Bump   up for air or ideas?

---

### Post by andybleaden on 2008-02-13
Anyone got any advice regards this. Any help would be gratefully recieved

---

