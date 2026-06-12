---
title: "Need 'copy' of /etc/fstab of a box with two cdrom, and also one with dvdrom and cdrw."
date: 2006-07-16
forum: Absolute Beginner Talk
---

### Post by Blur-king on 2006-07-16
I have two box, both on dapper with the above drives combo. I think dapper seem to a problem recognising the drives as separate one. My fstab showed only one cdrom. Can only use one drive at one time ie cannot listen to cds while doing other stuff. I think it also "screwed-up" my totem  and vlc as a result. Hoping to use a working fstab to try to remount the cdroms. Thanking all in advance.

---

### Post by cotcot on 2006-07-16
I have a DVDrom and a DVDrw. This is in my fstab :
> # /dev/cdrom	/mnt/cdrom	iso9660		auto,ro	0 0
# /dev/cdrom1	/mnt/cdrom1	iso9660		auto,rw	0 0

I do not think that there is code difference between dvd and cd; and between rom and rw.

---

### Post by bluecherry on 2006-07-16
This is my fstab 

> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               reiserfs notail          0       1
/dev/hda3       /home           reiserfs defaults        0       2
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda    /media/ipod    vfat    sync,user,noauto,umask=000    0 0


I've got a CDROM and a DVDRW. Both work and show up under "Computer" but my fstab doesn't mention both.

---

### Post by autocrosser on 2006-07-16
Interesting--I have two internal DVD's--one writer & one rom--one external firewire CD-burner & they all show up. My /etc/fstab only has a entry for a "cdrom0"--sounds like you may have a problem with configuring the devices--are you set-up as master/slave or cable select? Do the devices work as expected in (gasp) Windows?

---

### Post by Blur-king on 2006-07-17
Hi Thanks guys, just back from work. I think autocrosser maybe right. My drives are set as master and slave. it appears that the master seem to be working when palying video but both can read data disc though :confused: 

Are all yours on cable select (autocrosser). will try out to try to edit the fstab first. If it doe not work will open the box to set to cable select and see what happens. Thanks

---

### Post by Blur-king on 2006-07-17
Solve my problems, both box were hand me downs somehow the hardware were fixed up wrongly. The master of the IDE cable were attached to the slave drive and vice versa. All I need to do was to reset the drive setting after opening the bos and its system go. Anyone with similar problem may want to look along this line if all else fails....:oops:

---

### Post by autocrosser on 2006-07-17
Hey--I am glad it helped--I've seem a fair amount of systems set-up wrong or "kind'a" right--That would count as one of the top wrong configure types I've seen--Good job on finding it--You can't help what someone else messed up.......

---

### Post by OU812 on 2006-07-18
I have two dvd rws installed - both set to cable select. After installing ubuntu, only the "master" dvd was in fstab (probably because this was the drive used during installation). So, I had to edit fstab. But, to add a bit of info, /dev/hdc is the master device on the secondary ide cable and /dev/hdd is the slave device. You can, however, have them as /dev/cdrom and /dev/dvd, or as I have it /dev/cdrom0 and /dev/cdrom1. So, regardless of the /dev/name, linux still sees it as /dev/hdc and /dev/hdd.

Sorry if I may have missed the point.

john

---

