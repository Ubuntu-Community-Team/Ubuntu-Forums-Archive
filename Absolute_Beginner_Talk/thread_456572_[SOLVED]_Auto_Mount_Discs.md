---
title: "[SOLVED] Auto Mount Discs"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by carloslosgrande on 2007-05-27
Last night I noticed a thread
[http://ubuntuforums.org/showthread.php?t=456115](http://ubuntuforums.org/showthread.php?t=456115)
regarding auto mounting a disc.
Taurus' answer was very clear and direct but because of my ignorance, I'm not sure exactly what it means. At least in regards to my system.
to elaborate; my sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18885   151693731   83  Linux
/dev/sda2           18886       19452     4554427+   5  Extended
/dev/sda5           18886       19452     4554396   82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38346   308014213+  83  Linux
/dev/sdb2           38347       38913     4554427+   5  Extended
/dev/sdb5           38347       38913     4554396   82  Linux swap / Solaris
where sda is my main sys disc and sdb is my storage. each startup I use the gui to mount sdb, at /media/seagate
I think I must be reading the fdisk output wrong. Does boot = * mean that its the main disc?
I originally had separate OS on each disc but sort of broke the one on sdb (xorg) so now its just the storage.

my /etc/fstab looks like this;

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c174c1a9-0ff0-459f-bd96-d4ef5de3ae8f /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=27fee279-a1e2-4a08-ad51-ab672d98493b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

It looks like ChrisCummins has 1 disc, so why wouldn't it mount automatically anyway as it must be the main system disc??
I'm really just after a way to auto mount my second disc at startup without changing the current disc name/dir setup.
It isn't really important as doing it each startup is no great hardship I'm just trying to understand how this stuff works.
No doubt my description lacks important details, so I apologise in advance.
Any and all advice welcome.

---

### Post by overdrank on 2007-05-27
> **carloslosgrande said:**
> Last night I noticed a thread
[http://ubuntuforums.org/showthread.php?t=456115](http://ubuntuforums.org/showthread.php?t=456115)
regarding auto mounting a disc.
Taurus' answer was very clear and direct but because of my ignorance, I'm not sure exactly what it means. At least in regards to my system.
to elaborate; my sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18885   151693731   83  Linux
/dev/sda2           18886       19452     4554427+   5  Extended
/dev/sda5           18886       19452     4554396   82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38346   308014213+  83  Linux
/dev/sdb2           38347       38913     4554427+   5  Extended
/dev/sdb5           38347       38913     4554396   82  Linux swap / Solaris
where sda is my main sys disc and sdb is my storage. each startup I use the gui to mount sdb, at /media/seagate
I think I must be reading the fdisk output wrong. Does boot = * mean that its the main disc?
I originally had separate OS on each disc but sort of broke the one on sdb (xorg) so now its just the storage.

my /etc/fstab looks like this;

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c174c1a9-0ff0-459f-bd96-d4ef5de3ae8f /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=27fee279-a1e2-4a08-ad51-ab672d98493b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

It looks like ChrisCummins has 1 disc, so why wouldn't it mount automatically anyway as it must be the main system disc??
I'm really just after a way to auto mount my second disc at startup without changing the current disc name/dir setup.
It isn't really important as doing it each startup is no great hardship I'm just trying to understand how this stuff works.
No doubt my description lacks important details, so I apologise in advance.
Any and all advice welcome.

HI mounting a partition is hard for me anyway and Taurus is a great help. I would suggest reading this link 

and make sure you ***_backup please make sure you backup_***. I hope this will be of some help. Good luck! :p
Man I feel like a *** wrong link sorry 
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by alienexplorers on 2007-05-28
Read this about mounting file systems.
> [http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)

---

### Post by ugm6hr on 2007-05-28
> **carloslosgrande said:**
> 

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18885   151693731   83  Linux
/dev/sda2           18886       19452     4554427+   5  Extended
/dev/sda5           18886       19452     4554396   82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38346   308014213+  83  Linux
/dev/sdb2           38347       38913     4554427+   5  Extended
/dev/sdb5           38347       38913     4554396   82  Linux swap / Solaris

my /etc/fstab looks like this;

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c174c1a9-0ff0-459f-bd96-d4ef5de3ae8f /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=27fee279-a1e2-4a08-ad51-ab672d98493b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0



If you are using the second drive just for storage (and are not planning to reinstall an OS), you can delete the swap partition on it with GParted (it will free up that unused space).

And the way to automount it is clearly described here:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

Just replace the "/dev/hda5" with "/dev/sdb1", "/storage" with "/media/seagate" and "marie:marie" with "*yourusername*:*yourusername*"

---

### Post by carloslosgrande on 2007-05-28
Hey ugm6hr, thats it! you guys are great.
I should have known to look for Aysiu/psychocats, his stuff has helped me before. I was just a little confused by what I saw last night.
Thanks also for the notes about changing the various names, yes its obvious, but I don't always see it.

Also, this worked for me because it was clear and simple which is what I always need. I only really began learning about computing systems a few months ago, even though I've been using them for years.

Long term beginner.

---

### Post by ugm6hr on 2007-05-28
I'm a beginner in Linux too.  Only using Linux for 3 months, and Xubuntu for 2 weeks.  But I think these forums are great.  

I had the benefit of having just done what you wanted to do with my files partition.  And I was having the same thoughts about editing the instructions for my setup - so glad I could help ;)

---

