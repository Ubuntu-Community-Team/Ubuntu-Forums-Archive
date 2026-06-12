---
title: "NTFS support screwing w/ fstab and more"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by Darth_tater on 2006-11-22
with all the controversy over the WGA and EULA of vista, i decided i needed a change, and the ubuntu community was looking good.

i have a nearly perfect setup now, my two remaining gripes are that i can not access (read: write to) my NTFS volumes.

i have tried following the how to on ubuntuguide.org but i still can not write to my NTFS partitions.

here is the contents of my /etc/fstab file

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=0c2674e1-ba00-4d73-8cca-e1c72eb886a4 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
#UUID=A69CFEC79CFE9153 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=6F74068655E1EB0D /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb1
UUID=7C70EFA670EF64FC /media/sdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=32b5e371-d722-4faa-bb29-3cfa04e76056 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

#added
/dev/sda1   /media/windows/sda1    ntfs-3g    defaults,locale=en_US.utf8    0    0

``` 

sda1, sda2, sdb1 are all NTFS and are required for my windows OS's 
te last line is where i attempted to add NTFS write support for one partition (to see if i could get it to work.)  needless to say, it didn't.

sda1 is not automatically mounted to /media/windows/sda1, and i have to do it manually, and only then i can not access it unless i launch Nautilus as rot (sudo Nautilus) and even then i can not write to the file system.

please help (why cant i write to it?  did i mess up in the fstab file?) thanks

your help is appreciated

---

### Post by steve.horsley on 2006-11-22
try this line instead: 
> /dev/sda1   /media/windows/sda1    ntfs-3g    umask=0,locale=en_US.utf8    0    0
A umask of 0 says anyone can read/write that partition.

---

### Post by rlozano on 2006-11-22
did you install the ntfs-3g already? without it, you cannot write to your ntfs partition.

---

### Post by Darth_tater on 2006-11-22
i did infact install it, with this command.

sudo apt-get install ntfs-3g

---

### Post by Darth_tater on 2006-11-23
Help.... it still wont work :(

here is my fstab file

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=0c2674e1-ba00-4d73-8cca-e1c72eb886a4 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
#UUID=A69CFEC79CFE9153 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda2
#UUID=6F74068655E1EB0D /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb1
UUID=7C70EFA670EF64FC /media/sdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=32b5e371-d722-4faa-bb29-3cfa04e76056 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

#added
#sda1 xp pro corp x64
UUID=A69CFEC79CFE9153 /media/sda1 ntfs-3g umask=0,locale=en_US.utf8 0 0 
#sda2 vista 32
UUID=6F74068655E1EB0D /media/sda2 ntfs-3g umask=0,locale=en_US.utf8 0 0 

```

here is the result of (sudo mount)

```
karl@x64:~$ sudo mount 
/dev/sda6 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
/dev/sda1 on /media/sda1 type ntfs (rw)
/dev/sda2 on /media/sda2 type ntfs (rw)

```

however, when i try to go to the /media/sda* folder (in nautilus)
i get an error saying that i do not have permission.

also, when i am in terminal, i cannot copy things to the ntfs partition (even as root)

Help!!

---

### Post by taurus on 2006-11-23
Try to remove the "umask=0" from both NTFS entries and add "defaults" to them!!!

```

#added
#sda1 xp pro corp x64
UUID=A69CFEC79CFE9153 /media/sda1 ntfs-3g defaults,locale=en_US.utf8 0 0 
#sda2 vista 32
UUID=6F74068655E1EB0D /media/sda2 ntfs-3g defaults,locale=en_US.utf8 0 0

```

---

### Post by Darth_tater on 2006-11-23
well, i think that may have worked.

after i maded the suggested changes to my fstab file, i "sudo umount -a" then  "sudo mount -a"

hers what i got

```
karl@x64:~$ sudo umount -a
Password:
umount: /dev: device is busy
umount: /proc/bus/usb: device is busy
umount: /var/run: device is busy
umount: /sys: device is busy
umount: /: device is busy
karl@x64:~$ sudo mount -a
Failed to mount '/dev/disk/by-uuid/A69CFEC79CFE9153': Operation not supported
Mount is denied because the NTFS journal file is unclean. Choices are:
 A) Shutdown Windows properly.
 B) Click the 'Safely Remove Hardware' icon in the Windows taskbar
    notification area before disconnecting the device.
 C) Use 'Eject' from Windows Explorer to safely remove the device.
 D) If you ran chkdsk previously then boot Windows again which will
    automatically initialize the journal.
 E) Run 'ntfsfix' on Linux which will reset the NTFS journal.
 F) Mount the volume read-only by using the 'ro' mount option.
Error opening partition device: No such file or directory
Failed to startup volume: No such file or directory
Failed to mount '/dev/disk/by-uuid/6F74068655E1EB0D': No such file or directory 

```

i understnad what happened to the first partition and i plan to fix that in a few min (re-boot into windows and run chkdsk)
the second error throws me, however...?

thanks for your quick reply, btw.

---

### Post by taurus on 2006-11-23
Just reboot...

---

### Post by Darth_tater on 2006-11-23
rebooting didnt work until i chaged hte UUID to the actual system file (/dev/sda*)

here is the updated part of my sftab

```
#added
#sda1 xp pro corp x64
/dev/sda1 /media/sda1 ntfs-3g defaults,locale=en_US.utf8 0 0 
#sda2 vista 32
/dev/sda2 /media/sda2 ntfs-3g defaults,locale=en_US.utf8 0 0 

```

however, only the sda2 partition works (its automatically mounted and writeable!!!)

the sda1 partition does not work.... i have to manually mount it and even then, i can only access it through sudo nautilus

---

### Post by taurus on 2006-11-23
What is the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by Darth_tater on 2006-11-23
> **taurus said:**
> What is the output of this command from a terminal?

```
sudo fdisk -l
```

im in xxp ATM... (sadly, there is no easy way to get office 07 working in Linux) and ill post back when i am able to boot into Ubuntu again.

edit: other than vmware, is there a way to get office 07 installed?

---

### Post by Darth_tater on 2006-11-23
here it is... but before you go further... i have fixed it.. i jsut had to keep tewaking my fstab file and rebooting.  unfortunatly sudo umount -a dosent work... a reboot is required
```
l@x64:~$ sudo fdisk -l
Password:

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38248   307227028+   7  HPFS/NTFS
/dev/sda2           43542       48641    40965750    7  HPFS/NTFS
/dev/sda3           38249       43541    42516022+   f  W95 Ext'd (LBA)
/dev/sda5           43348       43541     1558273+  82  Linux swap / Solaris
/dev/sda6           38249       43347    40957654+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
16 heads, 63 sectors/track, 486344 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      486340   245115328+   7  HPFS/NTFS

```

---

### Post by Darth_tater on 2007-01-02
i hate to digg this back up, but...

ive got a problem w/ my vista partition again.

here is the contents of my etc/fstab file

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
# /dev/sda1
#UUID=A69CFEC79CFE9153 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda2
#UUID=6F74068655E1EB0D /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb1
#UUID=7C70EFA670EF64FC /media/sdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=32b5e371-d722-4faa-bb29-3cfa04e76056 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

#added
#sda1 xp pro corp x64
/dev/sda1 /media/sda1 ntfs-3g defaults,locale=en_US.utf8 0 0 
#sda2 vista 32
/dev/sda2 /media/sda2 ntfs-3g defaults,locale=en_US.utf8 0 0 
#sdb1 media/stuff drive
/dev/sdb1 /media/sdb1 ntfs-3g defaults,locale=en_US.utf8 0 0 
UUID=0c2674e1-ba00-4d73-8cca-e1c72eb886a4 /                    ext3       defaults              1 1


and hers what i get when i run "mount -t ntfs-3g /dev/sda2 /media/sda2"

```
karl@x64:~$ sudo mount -t ntfs-3g /dev/sda2 /media/sda2 
Failed to startup volume: Invalid argument
Failed to mount '/dev/sda2': Invalid argument
The device '/dev/sda2' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

```

any ideas?  i only reinstalled vista, and i haven't heard of it using a different type of NTFS.  thanks in advance

(again, sorry to bring this back up.... but its better than me posting a new thread, right?)

---

