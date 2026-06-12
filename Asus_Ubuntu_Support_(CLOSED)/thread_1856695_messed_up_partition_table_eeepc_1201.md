---
title: "messed up partition table eeepc 1201"
date: 2011-10-08
forum: Asus Ubuntu Support (CLOSED)
---

### Post by rohit.bhosale on 2011-10-08
* I was trying to check if I can take a backup of asus recovery partition on my eeepc 1201. I have Ubuntu 11.04 and windows 7 on the machine. My grub loader it self shows the option to boot in Ubuntu or Windows or windows recovery. 
* I chose recovery - it gave me asus recovery console as expected - it had 3 options recover, backup and exit. I clicked on backup and then hit cancel.
* it gave a little box that said "initializing" - this is where I did a mistake. I waited a bit and hard booted the machine. 
* then again chose recovery partition from grub loader! it never came up! 
* I booted back in ubuntu - it failed to automount one of the FAT32 drives but it did mount my windows C drive. it shows contents too. (however windows 7 also wont boot - like recovery partition, it also gets stuck at logo)
* now when I see the file manager, it shows /dev/sda100 till sda 255! all 3.9 GB swap! It actually shows up my drive D (which was FAT) data. They all show same data - I tried mounting a few partitions out of 155 options I see!

How do i fix this?

---

### Post by rohit.bhosale on 2011-10-08
output of df -h as I go on mounting these swap partitions


$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              58G   24G   31G  44% /
none                  995M  1.7M  994M   1% /dev
none                 1002M  492K 1001M   1% /dev/shm
none                 1002M  316K 1001M   1% /var/run
none                 1002M     0 1002M   0% /var/lock
/dev/sda1              81G   32G   49G  40% /media/c
/dev/sda2              15G   14G  2.0G  88% /media/86F4-D40A
/dev/sdb1             466G  325G  142G  70% /media/Iomega_HDD
/dev/sda101            37G  9.0G   28G  25% /media/74F6-A263
/dev/sda19             37G  9.0G   28G  25% /media/74F6-A263_
/dev/sda149            37G  9.0G   28G  25% /media/74F6-A263__


last line gets repeated then on with extra "_" for each new entry!

I opened Disk Utility - and tried to check NTFS partition for errors - it failed though - it did not allow me to unmount that drive. Partition Type for all was shown "unknown"

---

### Post by rohit.bhosale on 2011-10-08
CFDisk returns this


FATAL ERROR: Bad primary partition 3: Partition ends in the final partial cylind

---

### Post by coffeecat on 2011-10-09
You have a corrupted partition table. The easiest way to get an overview of your system is to run the boot script. Boot into Ubuntu and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script and post the contents of your RESULTS.txt file between [noparse]```
 and 
```[/noparse] tags.

---

