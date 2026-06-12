---
title: "Invalid mount option when trying to use USB"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by nokcin on 2007-10-13
I am running into an issue where I am not able to use the first USB devise I plug into the computer.  When I plug it in I get the following message:

     Invalid mount option when attempting to mount the volume 'UDISK 20X'.

However, when I plug in a second and or third device they both mount and operate normally (it does not matter the order they are plugged in, the first always returns the same error).  I loaded Feisty from a USB flash disk and I am assuming that that is the cause of my problems, but I am unable to rectify the problem.  The first device shares the same mount point as cdrom0 both have /dev/sdb1 (bolded below)

**_fdisk -l with one use device_**

laptop:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1275    10241406    7  HPFS/NTFS
/dev/sda2            1276        4490    25824487+  83  Linux
/dev/sda3            4491        4614      996030   82  Linux swap / Solaris
/dev/sda4            4615        4864     2008125    b  W95 FAT32

Disk /dev/sdb: 515 MB, 515899392 bytes
16 heads, 32 sectors/track, 1968 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

   Device Boot      Start         End      Blocks   Id  System
**/dev/sdb1**   *           1        

**_fstab_**
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=022248e1-aae2-4e33-a755-11997a2a34aa /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1 - if wanted to automount uncomment following line
#UUID=60C02183C0216090 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda4
UUID=404D-F825  /media/sda4     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=7ccdf644-442d-4e68-86f0-88e5214fc6c0 none            swap    sw              0       0
**/dev/sdb1**       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto     0       0


**_fdisk with 2 devices_**
laptop:~$ sudo fdisk -l
Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1275    10241406    7  HPFS/NTFS
/dev/sda2            1276        4490    25824487+  83  Linux
/dev/sda3            4491        4614      996030   82  Linux swap / Solaris
/dev/sda4            4615        4864     2008125    b  W95 FAT32

Disk /dev/sdb: 515 MB, 515899392 bytes
16 heads, 32 sectors/track, 1968 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1968      503792    6  FAT16

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       14593   117218241    c  W95 FAT32 (LBA)

Thanks in advanced for the help!

---

### Post by prof1337 on 2007-10-21
I had this same problem after installing Gutsy from a USB drive on a Dell D400 using the method found here:
[http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/]("http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/")

My fstab looked like this:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=de408021-fc5b-4333-a795-1bcc824eb2a0 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=6600d3bf-4b35-449d-9986-43c1bca19d5c /boot           ext3    defaults        0       2
# /dev/sda2
UUID=f470579e-d24e-4ea4-a6d1-91e1e858d463 none            swap    sw              0       0
/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```

I commented out the last line and my USB drive mounted correctly.

```
#/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```

I hope this helps!

---

### Post by clarkkent435 on 2008-05-26
This post is a winner - I has the same problem on Gutsy, installed from a USB drive. Commenting out the sdb1 entry in /etc/fstab solves the problem.

---

### Post by ceagan on 2008-07-10
This same issue happened to me after I re-installed with the latest version of Ubuntu. Upgrading doesn't seem to replace the /etc/fstab file so it didn't show up until I did a clean install. I imagine it has something to do with the fstab file saying that the /dev/sdb1 is going to be udf,iso9660 when in fact could be FAT. Anyway, this was really bugging me but I have it fixed now. Is there a bug in launchpad for this yet?

---

### Post by ipmccauley on 2008-07-10
This fixed my issue!

My fstab looked like:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=f8e352f8-aed9-40d6-9c2c-0d9f5ae6053c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=5cd8aaf7-26d2-4939-a676-533e833ad94d none            swap    sw              0       0
/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

I tried to comment out the last line first, issue persisted.

I then commented out both lines, and IT WORKED!

My new Fstab file looks like:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=f8e352f8-aed9-40d6-9c2c-0d9f5ae6053c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=5cd8aaf7-26d2-4939-a676-533e833ad94d none            swap    sw              0       0
#/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

Thank you for this great fix.

---

### Post by chukkers on 2008-07-15
i also installed from a usb drive and had the same issue. glad this sorted thanx for the help.

---

### Post by metalchef on 2008-07-16
I also encountered this problem...

thanks folks, for helping out (I'm still a bit of an ubuntu noob)

:guitar:

---

