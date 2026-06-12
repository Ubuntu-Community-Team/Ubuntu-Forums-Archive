---
title: "USB drives are not automounted"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by shafin on 2008-02-08
Recently my ubuntu box has stopped mounting Pen drives. It has been loading them finely,but now,it just dont do anything when I plug in a pen drive.

Please Help!

Also I wonder if this is related to [this problem]("http://ubuntuforums.org/showthread.php?t=686539"),as they started at the same time.

---

### Post by finer recliner on 2008-02-09
plug a thumb drive into the computer and post the output of:

```
sudo fdisk -l
```
(display what drives are recognized)

```
lsusb
```
(display what devices are currently plugged into USB slots)

---

### Post by shafin on 2008-02-10
sudo fdisk -l gives the following output:
```
Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfe7fb0aa


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1275    10241406    7  HPFS/NTFS
/dev/sda2            1276       10011    70171920    f  W95 Ext'd (LBA)
/dev/sda5            1276        3443    17414428+   7  HPFS/NTFS
/dev/sda6            3444        5483    16386268+   7  HPFS/NTFS
/dev/sda7            5484        5516      265041   82  Linux swap / Solaris
/dev/sda8            5517        6665     9229311   83  Linux
/dev/sda9            6666        8578    15366141    7  HPFS/NTFS
/dev/sda10           8579       10011    11510541    7  HPFS/NTFS

Disk /dev/sdb: 1021 MB, 1021125120 bytes
32 heads, 63 sectors/track, 989 cylinders
Units = cylinders of 2016 * 512 = 1032192 bytes
Disk identifier: 0xb9bf24dc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         989      996788+   6  FAT16

```

Here /dev/sdb is my pen drive.

 lsusb gives this output
```
 Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 0781:5406 SanDisk Corp. 
Bus 001 Device 001: ID 0000:0000  

```

Here my Sandisk drive is also recognized,but when I try to mount it,
I get this:
```
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 0781:5406 SanDisk Corp. 
Bus 001 Device 001: ID 0000:0000  
```

here is the /etc/fstab file
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda10
UUID=3d486e29-da12-4151-b886-52ca5cc7044e /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=B8C08833C087F5C2 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=1C14ABF714ABD1D6 /media/sda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda6
UUID=401808F81808EEAA /media/sda6     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda8
UUID=86CCE8F6CCE8E183 /media/sda8     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda9
UUID=E2DCF808DCF7D4AF /media/sda9     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda7
UUID=589bf42f-1988-4828-b41f-46e7724efe6e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```

---

### Post by PmDematagoda on 2008-02-10
Post the outputs of:-
```
ls /media
```
and
```
cat /etc/mtab
```

---

### Post by shafin on 2008-02-11
ls /media:
cdrom  cdrom0  sda1  sda5  sda6  sda8  sda9



 cat /etc/mtab:
```
/dev/sda8 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.22-14-generic/volatile tmpfs rw 0 0
/dev/sda1 /media/sda1 fuseblk rw,nosuid,nodev,allow_other,default_permissions,blksize=4096 0 0
/dev/sda5 /media/sda5 fuseblk rw,nosuid,nodev,allow_other,default_permissions,blksize=4096 0 0
/dev/sda6 /media/sda6 fuseblk rw,nosuid,nodev,allow_other,default_permissions,blksize=4096 0 0
/dev/sda9 /media/sda8 fuseblk rw,nosuid,nodev,allow_other,default_permissions,blksize=4096 0 0
/dev/sda10 /media/sda9 fuseblk rw,nosuid,nodev,allow_other,default_permissions,blksize=4096 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
```

---

### Post by PmDematagoda on 2008-02-11
Assuming the sdb1 is the path of the drive, try manually mounting the drive:-

1) Make a folder in /media:-
```
sudo mkdir /media/test
```

2) Mount the drive to the created directory using:-
```
sudo mount -t vfat /dev/sdb1 /media/test
```

3) Then move to the go to the test directory and see if the contents of your pen drive are being displayed.

---

### Post by shafin on 2008-02-11
Thanks a lot!!
it worked.Is there any way to automate it?

BTW, I've found out the problem with hotplugging is probably related to HAL not initializing. when I tried to go to System->Preferences->Removable Drives and Media It said that I did not have HALD running,and when I log on,it gives me a message saying that HAL failed to initialize.If you can help me in finding out and solving that problem, I'd be really grateful.

---

### Post by PmDematagoda on 2008-02-11
Post the output when executing:-
```
sudo /etc/init.d/hal start
```

---

### Post by shafin on 2008-02-11
I got the following output:
sudo /etc/init.d/hal start
[B] * Starting Hardware abstraction layer hald                              [ OK ] 
[/B]


After this,the USB drives hotplugged properly. Now, I can get HAL working in this process,but what can be cause of it failing to initialize in the first place and can you give me some suggestions on it.

And again, thanks :)

---

### Post by PmDematagoda on 2008-02-12
Do this:-

1) Open the rc.local file for editing using:-
```
gksudo gedit /etc/rc.local
```

2) Add the line to start HAL to make the file look like this:-
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
/etc/init.d/hal start
exit 0
```
Save the file and see if your problem is solved.

---

