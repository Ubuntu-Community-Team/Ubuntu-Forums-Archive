---
title: "acess external hdd as root"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by mikecomua on 2007-08-09
Hi, I have an external HDD, which I want to use with Kubuntu, but the problem is when I try to access it it says: 
Unable to enter file:///media/FreeAgent. You do not have access rights to this location.
I have tried to change the settings, but nothing works.What should I do?

---

### Post by Rocket2DMn on 2007-08-09
Can you please post the outputs of 
```
cat /etc/fstab
sudo fdisk -l
```
If you haven't already, we will add your external hard drive to fstab with the proper permissions.

---

### Post by mikecomua on 2007-08-09
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/sda3
UUID=97d3a1f4-6ad2-4dad-8a64-0a68057e9ca2 / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/sda1
UUID=07D6-0819 /media/sda1 vfat defaults,utf8,umask=007,uid=0,gid=46,auto,rw,nouser 0 1
# /dev/sda2
UUID=26DC1121DC10ED35 /media/sda2 ntfs defaults,nls=utf8,umask=007,uid=0,gid=46,auto,rw,nouser 0 1
# /dev/sda4
UUID=44EF-6EED /offshare vfat defaults,utf8,umask=007,uid=0,gid=46,auto,rw,nouser 0 1
/dev/scd0 /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/sdb1 /media/FreeAgent auto user,atime,auto,rw,nodev,noexec,nosuid 0 0
<device> <mount\040point> auto users,atime,noauto,rw,nodev,noexec,nosuid 0 0
mike@Mike-Ubuntu-Laptop:~$ sudo fdisk -l

---

### Post by mikecomua on 2007-08-09
Doesn't work. Sorry:(

---

### Post by MenZa on 2007-08-09
There's no output of sudo fdisk -l.

In addition to these two outputs, could you also paste the output of *cat /etc/mtab*?

---

### Post by mikecomua on 2007-08-09
cat: /etc/mtab?: No such file or directory

---

### Post by Rocket2DMn on 2007-08-09
I'm going to assume the drive you're trying to access is /dev/sdb1
The fstab entry should look more like this
```
/dev/sdb1 /media/FreeAgent  ntfs-3g  defaults,locale=en_US.utf8  0  0
```
Then
```
sudo chmod 777 /media/FreeAgent
```
To edit that fstab file:
```
gksudo gedit /etc/fstab
```

BTW, do you have ntfs-3g installed?  If not:
[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

### Post by MenZa on 2007-08-09
I'd probably use something more along the lines of user,sync,auto... I'm not sure I like defaults as much.

---

### Post by Rocket2DMn on 2007-08-09
> **MenZa said:**
> I'd probably use something more along the lines of user,sync,auto... I'm not sure I like defaults as much.

I'm inclined to agree, I just gave something simple and straightforward.  I'm not on my Ubuntu laptop to check my settings and pass them along.  There are more details on these options about halfway down the page here: [https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

---

### Post by MenZa on 2007-08-09
There's a really good article on fstab here: [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

### Post by mikecomua on 2007-08-09
Here's what it gave me:
mike@Mike-Ubuntu-Laptop:~$ /dev/sdb1 /media/FreeAgent  ntfs-3g  defaults,locale=en_US.utf8  0  0
bash: /dev/sdb1: Permission denied
mike@Mike-Ubuntu-Laptop:~$ sudo chmod 777 /media/FreeAgent
chmod: changing permissions of `/media/FreeAgent': Read-only file system
mike@Mike-Ubuntu-Laptop:~$ gksudo gedit /etc/fstab
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
mike@Mike-Ubuntu-Laptop:~$

---

### Post by Rocket2DMn on 2007-08-09
Errr, lol, no.  That line goes in the fstab file
```
gksudo gedit /etc/fstab
```
It should replaced the current line for /dev/sdb1
```
/dev/sdb1 /media/FreeAgent ntfs-3g defaults,locale=en_US.utf8 0 0
```
This is assuming that sdb1 is the correct partition.  If you can get us output from
```
sudo fdisk -l
``` that would be great.  Note that -l is a lowercase L.

---

### Post by mikecomua on 2007-08-10
THis is my configured fstab file:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/sda3
UUID=97d3a1f4-6ad2-4dad-8a64-0a68057e9ca2 / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/sda1
UUID=07D6-0819 /media/sda1 vfat defaults,utf8,umask=007,uid=0,gid=46,auto,rw,nouser 0 1
# /dev/sda2
UUID=26DC1121DC10ED35 /media/sda2 ntfs defaults,nls=utf8,umask=007,uid=0,gid=46,auto,rw,nouser 0 1
# /dev/sda4
UUID=44EF-6EED /offshare vfat defaults,utf8,umask=007,uid=0,gid=46,auto,rw,nouser 0 1
/dev/scd0 /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
dev/sdb1 /media/FreeAgent ntfs-3g defaults,locale=en_US.utf8 0 0
<device> <mount\040point> auto users,atime,noauto,rw,nodev,noexec,nosuid 0 0

Then when I typed sudo  fdisk -l:
Disk /dev/sda: 78.5 GB, 78518522880 bytes
255 heads, 63 sectors/track, 9546 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7        6694    53721360    7  HPFS/NTFS
/dev/sda3            6695        8926    17928540   83  Linux
/dev/sda4            8927        9545     4972117+  db  CP/M / CTOS / ...

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241    7  HPFS/NTFS

---

### Post by Rocket2DMn on 2007-08-10
Your disk should be fine.  You can mount with
```
sudo mount -a
```

---

### Post by mikecomua on 2007-08-11
The problem was eliminated by converting the partition to FAT32.:lolflag:

---

