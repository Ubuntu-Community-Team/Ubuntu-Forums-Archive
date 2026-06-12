---
title: "format drive"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by carverj on 2007-04-04
Hi there,
              Just wondering if there is an easy command to format a hard disk?
If I type cfdisk /dev/hda in terminal, will that do it?
Cheers

---

### Post by devnulljp on 2007-04-04
I hope you're not booting from /dev/hda and trying to format it...
Anyways, fdisk will format a drive for you
try man fdisk and man mkfs for instructions, but basically
sudo fdisk /dev/hdx
follow the instructions to partition the drive...you'll finish up with w to write the new partition table and exit
Then use mkfs to create a usable filesystem
Something like this for ext3
mkfs.ext3 -b 4096 /dev/hdb1
or you could use gui apps  like qtparted or gparted, but cli is cleaner and less buggy.

---

### Post by carverj on 2007-04-04
Hi, I'm following lucky 13's instructions at [http://damnsmalllinux.org/cgi-bin/fo...048;hl=install](http://damnsmalllinux.org/cgi-bin/fo...048;hl=install)
So will 
> mkfs.ext3 -b 4096 /dev/hdb1
be sufficient to create the Damn Small Linux partition?
He also says to make swap by changing type to 82 Linux Swap/Solaris
So does this mean I can use the command
mkfs.swap/Solaris -b 4096 /dev/hdb1 (he is putting swap first...don't know why?) 
and then sudo mkfs.ext3 -b 4096 /dev/hdb(possibly  hda in my case)(0 or 1...I don't know, 0 is the first partition isn't it?)

---

