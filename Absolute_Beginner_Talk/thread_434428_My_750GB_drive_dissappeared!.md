---
title: "My 750GB drive dissappeared!"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by rubix64 on 2007-05-05
O.K. so  maybe that was overstating it just a little.:) 

I have 2 drives, the master a 330gb and a 750gb slave. I just did an ubuntu install(s) and love it but Im wondering why its labeled the master drive Floppy1 and the 750 (that it registered when I partitioned the master) just isn't there?

do I need to somehow format the 750 slave drive w/ Live cd?

---

### Post by cypherzero on 2007-05-05
You shouldn't need to if it's already been formatted.
You might want to try manually mounting it and/or checking your fstab file for errors.

---

### Post by rubix64 on 2007-05-05
how do I manually mount it?


thanks!

---

### Post by rubix64 on 2007-05-06
Update!!

use of the 'sudo fdisk -l /dev/sdb' where sdb is my 750gb hd yielded this:


Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sdb doesn't contain a valid partition table


Sooooo.....what now...is there a command line function to format or partition the drive? 

Any ideas? All help is much appreciated.

---

### Post by JJNova on 2007-05-06
This is the method I have used to partition, format, mount, and auto-mount all of the hard drives in my box (3 besides the primary).

Hope this works for you also.
[http://daryl.learnhouston.com/2006/05/03/adding-a-hard-drive-to-a-ubuntu-linux-box/](http://daryl.learnhouston.com/2006/05/03/adding-a-hard-drive-to-a-ubuntu-linux-box/)

---

### Post by nalmeth on 2007-05-06
sudo mount /dev/nameofdevice
sudo umount /dev/nameofdevice

Gparted is a graphical partitioning tool.

You must unmount a partition before doing ANYTHING to it, and you must use extreme caution when using this, don't alter the wrong partition or device.

If you try running it as normal user, it will tell you it can be a Weapon of Mass Destruction, and only root can use it. Its true.

run it with 
gksu gparted

not with sudo

EDIT: About Master/Slave, have you checked those settings on the drives themselves?

---

### Post by rubix64 on 2007-05-06
O.K. so with:

 gksu gparted

I was able to successfully partition and format the drive "sdb1"  and when I " sudo flist -l" i get:

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       35157   282398571   83  Linux
/dev/sda2           35158       36481    10635030    5  Extended
/dev/sda5           35158       36481    10634998+  82  Linux swap / Solaris

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       91201   732572001   83  Linux



BUT sdb1 still doest show up in my 'places' and when I try 'mount /dev/sdb1" I get:

nomad@Kitabu:~$ sudo mount /dev/sdb1
mount: can't find /dev/sdb1 in /etc/fstab or /etc/mtab
nomad@Kitabu:~$ sudo fdisk -l



.....any ideas?

---

### Post by rubix64 on 2007-05-06
Stop the presses. Problem fixed.

it was as simple as a reeboot.


Thanks for all the time and help you guys.

The force strong is in you nalmeth!

---

