---
title: "where's my logical drive?"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by cele on 2007-04-08
I'we created a new logical drive of 20GB size using Gparted. How and where to find this drive on Ubuntu 6.10? It should be FAT32 but not formated.

---

### Post by overdrank on 2007-04-08
> **cele said:**
> I'we created a new logical drive of 20GB size using Gparted. How and where to find this drive on Ubuntu 6.10? It should be FAT32 but not formated.

Hi, I am a little unsure of what you are asking. Did you add a partition or a additional drive? If it is Fat32 then it has been formatted?

---

### Post by cele on 2007-04-08
on my way of solwing that with
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by cele on 2007-04-09
I'we stucked...

my laptop disk look's like this...

**********************************************
cele@cele-laptop:~$ sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         637     5116671   83  Linux
/dev/hda2             638         703      530145   82  Linux swap / Solaris
/dev/hda3             704        3253    20482875    5  Extended
/dev/hda5             704        3253    20482843+   b  W95 FAT32
cele@cele-laptop:~$ sudo mount /dev/hda5 /home/cele/temp
**********************************************


my fstab look's like this...

**********************************************
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=e16b8e0d-7ebd-4d8e-8f40-a3e6626f4465 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda2
UUID=03d190d6-153b-4b2d-98f0-a681e5cf99ea none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
**********************************************

I'we created this /hda5 partition to be used from windows and to be shared from utleast 2 acc on my ubuntu (6.10). 
How to make it 2 be mounted always when i boot and shared  between account's under Ubuntu?

---

### Post by bulldog on 2007-04-09
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by cele on 2007-04-09
I have read that and I'm afread I might mess something with fstab file since it's little bit difrend in 6.10 that in 6.06 version.

---

### Post by overdrank on 2007-04-09
> **cele said:**
> I have read that and I'm afread I might mess something with fstab file since it's little bit difrend in 6.10 that in 6.06 version.

Hi there is a *great how to in the help in edgy at the top panel*. Here goes the instructions.
terminal command  sudo mkdir /media/windows
 next  back up  you fstab: sudo cp /etc/fstab /etc/fstab_backup

then edit your fstab  sudo gedit /etc/fstab
at the end of the file add   /dev/hda5 /media/windows   vfat   unmask=0222 0 0
save the file and there you go.
 You may have to reboot but hope this helps and good luck.

---

### Post by cele on 2007-04-09
after i did that i tried:

*********************************************
cele@cele-laptop:/media$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/hda5,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

*********************************************

and this is what i get?

---

### Post by cele on 2007-04-09
I managed to do something with:

/dev/hda5 /media/multimedia vfat iocharset=utf8,umask=0222 0 0

this line, and there was no error. But I still can't write to that device.

---

### Post by cele on 2007-04-09
I can write to that device with sudo command. How to do that form Gnome world, I mean File Browser?

---

### Post by antoz on 2007-04-09
here is an other link that offers lots of advice

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

