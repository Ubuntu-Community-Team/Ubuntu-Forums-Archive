---
title: "here we go again"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by Blond37 on 2007-06-06
well back to the same problem. i spent DAYS trying to get my internal hard drive- i have two- to mount and all and i rebooted and now its GONE...

[https://answers.launchpad.net/ubuntu/+question/7399](https://answers.launchpad.net/ubuntu/+question/7399)

---

### Post by Blond37 on 2007-06-06
well back to the same problem. i spent DAYS trying to get my internal hard drive- i have two- to mount and all and i rebooted and now its GONE...

[https://answers.launchpad.net/ubuntu/+question/7399](https://answers.launchpad.net/ubuntu/+question/7399)

---

### Post by mlind on 2007-06-06
hiya, please don't post multiple threads of the same subject.
[http://ubuntuforums.org/showthread.php?t=466360](http://ubuntuforums.org/showthread.php?t=466360)

---

### Post by Ek0nomik on 2007-06-06
> **Blond37 said:**
> well back to the same problem. i spent DAYS trying to get my internal hard drive- i have two- to mount and all and i rebooted and now its GONE...

[https://answers.launchpad.net/ubuntu/+question/7399](https://answers.launchpad.net/ubuntu/+question/7399)

Can you post the output of:

```
sudo fdisk -l
```

and

```
sudo cat /etc/fstab
```

---

### Post by Blond37 on 2007-06-06
> **Ek0nomik said:**
> Can you post the output of:

```
sudo fdisk -l
```

and

```
sudo cat /etc/fstab
```

tunder@tunder-desktop:~$ sudo fdisk -l
Password:

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4660    37431418+  83  Linux
/dev/hda2            4661        4865     1646662+   5  Extended
/dev/hda5            4661        4865     1646631   82  Linux swap / Solaris

Disk /dev/hdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       36481   293033601   83  Linux
tunder@tunder-desktop:~$ sudo cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=546f2505-f820-4b27-8e8f-08405beb7b8d /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=eb4db2d4-565e-4a43-8b76-fab214ccb128 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdb1 /mnt/hdb ext3 defaults 0 0

tunder@tunder-desktop:~$

---

### Post by Blond37 on 2007-06-06
> **mlind said:**
> hiya, please don't post multiple threads of the same subject.
[http://ubuntuforums.org/showthread.php?t=466360](http://ubuntuforums.org/showthread.php?t=466360)

i'm sorry i dont understand.

---

### Post by Ek0nomik on 2007-06-06
The 300GB partition is the one you can't get mounted I presume?

The 40GB partition is the one holding Ubuntu and the Swap?

---

### Post by Blond37 on 2007-06-06
> **Ek0nomik said:**
> The 300GB partition is the one you can't get mounted I presume?

The 40GB partition is the one holding Ubuntu and the Swap?


yup!

---

### Post by Ek0nomik on 2007-06-06
Well, I have an idea, but before I go ahead and share with you I want to research something quick.

I am currently at work, but I am done in 7 minutes, and it takes me 30 minutes to get home.  Once I get home, I'll shoot you a reply.  :)

---

### Post by Blond37 on 2007-06-06
> **Ek0nomik said:**
> Well, I have an idea, but before I go ahead and share with you I want to research something quick.

I am currently at work, but I am done in 7 minutes, and it takes me 30 minutes to get home.  Once I get home, I'll shoot you a reply.  :)

oh lord ok.. i just dont want to lose any data (AGAIN)

---

### Post by Blond37 on 2007-06-06
you can check out the thing on launch pad too..  see my original post here.. its all there but there was so much typed wrong and back and forth that i dont haver the directions in clear order.

---

### Post by Ek0nomik on 2007-06-06
> **Blond37 said:**
> oh lord ok.. i just dont want to lose any data (AGAIN)

I don't see why you would...  :)

---

### Post by Ek0nomik on 2007-06-06
Well, first of all, do you have a /mnt/hdb directory?

```
cd /mnt/
```

```
ls
```

I personally have USB External devices, so I haven't done an internal, but it should be fairly similar.

---

