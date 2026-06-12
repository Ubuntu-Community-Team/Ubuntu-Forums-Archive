---
title: "partitioning"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by darkaznmonkey on 2008-02-12
hi im completely new

on my computer i have two sets of hard drives which i both used in xp

and i want to be able to use both hard drives

every time i've tried, i could only access one of the hard drives

i want to completely change to ubuntu

but i'm confused on how to partition

my friend who said would help, is busy this week

so any and all help would be appreciated

---

### Post by Amstell on 2008-02-12
where can't you access the drives from?  g parted or what?

Couple more specifics would be good. 

I'll be glad to help

---

### Post by oedha on 2008-02-12
you may try gparted to work on partition.....
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
both HD can be used together.....depend on what is your design

---

### Post by darkaznmonkey on 2008-02-12
> **darkaznmonkey said:**
> hi im completely new

on my computer i have two sets of hard drives which i both used in xp

and i want to be able to use both hard drives

every time i've tried, i could only access one of the hard drives

i want to completely change to ubuntu

but i'm confused on how to partition

my friend who said would help, is busy this week

so any and all help would be appreciated

from inside unbuntu

i already have the os installed, its just out of the 640 gb i have, i only have about 300 now

---

### Post by darkaznmonkey on 2008-02-12
> **oedha said:**
> you may try gparted to work on partition.....
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
both HD can be used together.....depend on what is your design

uh i've downloaded gparted

but i have no idea how to install it...i'm still getting used to unbuntu i guess..

---

### Post by oedha on 2008-02-12
gparted is an iso...you have to burn it to a cd....then run it.....it's live cd

---

### Post by jan quark on 2008-02-12
read through this tutorials on gparted
perhaps they will take away some concerns

[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
[http://gparted.sourceforge.net/larry/livecd/main/livecd.htm](http://gparted.sourceforge.net/larry/livecd/main/livecd.htm)

---

### Post by housam on 2008-02-12
If you already have ubuntu installed , just type in the terminal ```
sudo fdisk-l
```
where -l is a small L , to view all the partitions you have. and then you can decide which to delete or to resize.

---

### Post by jan quark on 2008-02-12
to see what partitions are recognized
run the following terminal commands and post the output please

```

mount
```

```
sudo fdisk -l
```

```
cat /etc/fstab
```

---

### Post by darkaznmonkey on 2008-02-12
> **housam said:**
> If you already have ubuntu installed , just type in the terminal ```
sudo fdisk-l
```
where -l is a small L , to view all the partitions you have. and then you can decide which to delete or to resize.

sudo fdisk-l

---

### Post by darkaznmonkey on 2008-02-12
> **jan quark said:**
> to see what partitions are recognized
run the following terminal commands and post the output please

```

mount
```
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)

```
sudo fdisk -l
```
sudo: fdisk-l: command not found

```
cat /etc/fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=3cd37143-40bf-49bb-82c2-0d921da79c32 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb1
UUID=ed92ede0-cf19-497b-a64a-22101d665cb1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

---

### Post by Moop on 2008-02-12
> **darkaznmonkey said:**
> sudo fdisk-l

Copy and paste that into the terminal. You can find the terminal by going to Applications-Accessories-Terminal.

edit: i see you got that.

---

### Post by darkaznmonkey on 2008-02-12
> **Moop said:**
> Copy and paste that into the terminal. You can find the terminal by going to Applications-Accessories-Terminal.

darkaznmonkey@darkaznmonkey-desktop:~$ sudo fdisk-l

sudo: fdisk-l: command not found


weird...

---

### Post by darkaznmonkey on 2008-02-13
> **Moop said:**
> Copy and paste that into the terminal. You can find the terminal by going to Applications-Accessories-Terminal.

edit: i see you got that.

so what does it mean??? =0

---

### Post by housam on 2008-02-13
> **darkaznmonkey said:**
> darkaznmonkey@darkaznmonkey-desktop:~$ sudo fdisk-l

sudo: fdisk-l: command not found


weird...

make one space between fdisk and -l and try it again . it should work.

---

### Post by darkaznmonkey on 2008-02-13
> **housam said:**
> make one space between fdisk and -l and try it again . it should work.


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38913   312568641   83  Linux

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xae958f6c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641   82  Linux swap / Solar

---

### Post by housam on 2008-02-14
> **darkaznmonkey said:**
> Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38913   312568641   83  Linux

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xae958f6c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641   82  Linux swap / Solar

If this is all what you've got from the code ( sudo fdisk -l ) then I see that you have two drives, one of them (** sda1 ** ) is used completely as a root and the other one ( **sdb1** ) is used completely as a swap ( that's  why you  don't see it. ).

Now you have to know that a swap partition should not exceed 2 x RAM. which means that you have to partition your hard drives ( using a Gparted tool - on the ubuntu live cd ) . 
You can resize the first drive ( which has ubuntu ) to about 50 GB partition and create  another partition which can be used as data / music storage place.
Also the other drive will be resized to a 2 GB partition for the swap and create another partitions ( 2-3 ) to use it as you like ( you'll see these partitions in this case ).

---

