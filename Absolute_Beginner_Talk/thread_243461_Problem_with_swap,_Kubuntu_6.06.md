---
title: "Problem with swap, Kubuntu 6.06"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by CalvinChile on 2006-08-25
Hi, 
I just found out that my system is not using the swap partition. If I open the System Setting app, I can see that the swap partition is disabled ( 1 Gig at /dev/sda5) and if I try to enable I get an error:
"An error occurred while enabling swap partition /dev/sda5, the system reported: swapon:/dev/sda5 : Invalid argument"

The dmesg last line gives:
[17200502.400000] Unable to find swap-space signature

Any idea what is wrong and how to correct?

Thanks
Nicolas

uname -a
Linux Inspiron6400 2.6.15-26-686 #1 SMP PREEMPT Thu Aug 3 03:13:28 UTC 2006 i686 GNU/Linux

---

### Post by CalvinChile on 2006-08-25
Just to add more details, here is the fstab on my system

more /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
/dev/sda2 / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
/dev/sda5 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/sda1 /media/Windows ntfs nls=utf8,umask=0222,uid=0,gid=0,auto,rw,nouser 0 0
/dev/sda4 /home ext3 nodev,nosuid 0 2

---

### Post by amo-ej1 on 2006-08-25
it looks like /dev/sda5 is not recognized as a swap partition there are two things you can do:
a) first make REALLY REALLY REALLY sure that /dev/sda5 is the partition you wanted to have as a swap partition. 
b) 'format' it as a swap partition manually run as root (su/sudo)  'mkswap /dev/sda5' (see man mkswap for details) this will create a swap partition on /dev/sda5 and should get rid of the error complaining about the swap space signature. But od this only if you are really sure that it actually is the partition you wish to use as a swap partition

---

### Post by Fass on 2006-08-25
Try running

```
sudo mkswap -c /dev/sda5
```

and then retry swapon.

---

### Post by CalvinChile on 2006-08-25
Thanks amo-ej1 for the fast answer, I will give it a try. I'm pretty sure the 1G partition is the swap one, and is defined as swap in the Disk&Filesystem application inside System Settings

---

### Post by CalvinChile on 2006-08-25
It worked! thanks.

sudo mkswap -c /dev/sda5
Password:
Setting up swapspace version 1, size = 1093922 kB
no label, UUID=74903f10-6828-4e18-a04b-c7d6a12a2ebc

and then I enabled without any error output.

---

