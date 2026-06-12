---
title: "where is my hard disk dev file ???"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by Sasa_Ivanovic on 2007-01-09
I have two hard disks. And three partritions. I just formated my second HDD from ntfs to fat32 in order to be able to write changes :

First HDD :
1. Windows ( NTFS )
2. Ubuntu ( Ext3 )

Second :
1. nothing ( FAT32 )

When i start Ubuntu it doesn't automaticly mount my second HDD. So i have to use mount command but i can't find the dev file. Where is it ?

---

### Post by taurus on 2007-01-09
```
sudo fdisk -l
```

---

### Post by Sasa_Ivanovic on 2007-01-09
thanks, i mounted sucsessfully.

But it seems that when i reboot i have to mount it again, Can i avoid this ?

---

### Post by scj on 2007-01-09
To mount a disk at boot time edit /etc/fstab

---

### Post by taurus on 2007-01-09
```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by Sasa_Ivanovic on 2007-01-09
Do i have to umount the disk every time i want to restart or turn off the comp?
'Cause i've read somewhere that avoiding umount can 'cause problems...

---

### Post by Sasa_Ivanovic on 2007-01-09
here is my fstab :
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb2
UUID=bc4051a7-83ae-4ca2-980a-4fec84beb657 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=A28020EE8020CB1D /media/sda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb1
UUID=5218A4CD18A4B181 /media/sdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb5
UUID=3cd6bd16-8351-4327-9115-f9c5ca76ac53 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

```
what should i change ?

---

### Post by Sasa_Ivanovic on 2007-01-09
note : sda5 is the disk i want to mount, and it seems the ntfs format stayed in the file.

---

### Post by taurus on 2007-01-09
Did you format /dev/sda5 recently?  If you did, then the UUID may have changed and therefore, /etc/fstab can't mount it.  So, I would recommend you edit /etc/fstab and change the UUID for /dev/sda5 back to /dev/sda5.

```
/dev/sda5   /media/sda5     ntfs    defaults,nls=utf8,umask=007,gid=46   0     1
```
And you don't have to unmount it before you shutdown or reboot.  The system will do that for you.

---

### Post by Sasa_Ivanovic on 2007-01-09
> **taurus said:**
> Did you format /dev/sda5 recently?  If you did, then the UUID may have changed and therefore, /etc/fstab can't mount it.  So, I would recommend you edit /etc/fstab and change the UUID for /dev/sda5 back to /dev/sda5.

```
/dev/sda5   /media/sda5     ntfs    defaults,nls=utf8,umask=007,gid=46   0     1
```
And you don't have to unmount it before you shutdown or reboot.  The system will do that for you.
Yes i did format it. Just about five minutes ago.

"change the UUID for /dev/sda5 back to /dev/sda5"
how can i change something to itself ?

Could you edit my fstab file and post it here ?

---

### Post by taurus on 2007-01-09
```
gksudo gedit /etc/fstab
```

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb2
UUID=bc4051a7-83ae-4ca2-980a-4fec84beb657 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
/dev/sda5   /media/sda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb1
/dev/sdb1   /media/sdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb5
UUID=3cd6bd16-8351-4327-9115-f9c5ca76ac53 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

```

---

### Post by Sasa_Ivanovic on 2007-01-09
> **taurus said:**
> ```
gksudo gedit /etc/fstab
```

I'm not that dumb.

Thanks, i'll try this out right now.
The system is going down NOW.

---

### Post by Sasa_Ivanovic on 2007-01-09
doesn't work for some reason :

when Ubuntu boots i goto /media/sda5/
and there's nothing there

---

### Post by taurus on 2007-01-09
> **Sasa_Ivanovic said:**
> doesn't work for some reason :

when Ubuntu boots i goto /media/sda5/
and there's nothing there

But didn't you said you just formatted /dev/sda5!  Did you put anything in it since you formatted like a few minutes ago?

```
df -h
```

---

### Post by Sasa_Ivanovic on 2007-01-09
yes i put a dummy file to see if it works.
when i use :
```

mount -t vfat /dev/sda5 /media/somefolder

```
i can find the file in "somefolder"
while this way it's empty.

Also when i see the properties of somefolder it says : 120 GB free.
while this way it's 40 GB ( the disk where Ubuntu is installed has 40 GB free )

---

### Post by Sasa_Ivanovic on 2007-01-09
also i changed "ntfs" to "vfat" in your fstab.

---

### Post by Sasa_Ivanovic on 2007-01-09
df -h
```

sasa@Kanta:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb2             102G   53G   44G  55% /
varrun               1014M   80K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
procbususb             10M  124K  9.9M   2% /proc/bus/usb
udev                   10M  124K  9.9M   2% /dev
devshm               1014M     0 1014M   0% /dev/shm
lrm                  1014M   18M  997M   2% /lib/modules/2.6.17-10-386/volatile
/dev/sdb1              42G   28G   15G  66% /media/sdb1

```
note : the sdb1 is the partrition where Win is installed.

---

### Post by taurus on 2007-01-09
So is it ntfs or vfat?

```
sudo fdisk -l
```

---

### Post by Sasa_Ivanovic on 2007-01-09
As i've sad at the beginning of this thread :
```

sasa@Kanta:~$ sudo fdisk -l

Disk /dev/sda: 122.9 GB, 122941242880 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2       14946   120045712+   f  W95 Ext'd (LBA)
/dev/sda5               2       14946   120045681    b  W95 FAT32

Disk /dev/sdb: 160.0 GB, 160040803840 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        5471    43945776    7  HPFS/NTFS
/dev/sdb2            5472       18887   107764020   83  Linux
/dev/sdb3           18888       19457     4578525    5  Extended
/dev/sdb5           18888       19457     4578493+  82  Linux swap / Solaris

```

---

### Post by Sasa_Ivanovic on 2007-01-09
I commented out the line :
```

/dev/sda5   /media/sda5     vfat  
#  defaults,nls=utf8,umask=007,gid=46 0       1

```
And it works, for some unknown reason...
thanks for your help though.

---

