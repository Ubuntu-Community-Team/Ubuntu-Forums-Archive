---
title: "I can't mount my NTFS volumes!"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by cursebg on 2007-08-04
I used to do it by just clicking on the drives but now (I dont know why) when i do the procedure i get this:
[[IMG]http://img383.imageshack.us/img383/4379/screenshot1sa5.th.png[/IMG]](http://img383.imageshack.us/my.php?image=screenshot1sa5.png)

I've tried using the terminal, modifying th fstab file, installing ntfs-3g - nothing! Please help! :(

I'm using Ubuntu 7.04 :)

---

### Post by Inxsible on 2007-08-04
post the output of 
```
cat /etc/fstab
```and ```
sudo fdisk - l
```-l is lowercase L

---

### Post by Inxsible on 2007-08-04
oh and what is the theme that you are using? I like dark themes :)

---

### Post by AlexenderReez on 2007-08-04
you need to install ntfs-config ...refer this please --->


> [http://www.unix-tutorials.com/go.php?id=861](http://www.unix-tutorials.com/go.php?id=861)

[B]
UAResolved[/B]

---

### Post by cursebg on 2007-08-04
Here you are :)
The theme is great, you have the link at the bottom :)> root@r43264r32hf4236:/home/vicho# cat /etc/fstab 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=78eb77e9-786f-4f54-848a-9effa6ec7a75 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=AA24AD6B24AD3AE9 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=B87045F67045BBBE /media/hda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb5
UUID=468A-8087  /media/hdb5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb6
UUID=8D15-011A  /media/hdb6     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb7
UUID=D39F-81B9  /media/hdb7     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb2
UUID=69797447-7570-4198-9a1d-bddbd5d9010f none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdb5 /mnt/captive-noname captive-ntfs defaults,noauto 0 0
/dev/hdb6 /mnt/captive-noname2 captive-ntfs defaults,noauto 0 0
/dev/hda5 /mnt/captive-noname3 captive-ntfs defaults,noauto 0 0
/dev/hdb7 /mnt/captive-noname4 captive-ntfs defaults,noauto 0 0
/dev/hda1 /mnt/captive-noname5 captive-ntfs defaults,noauto 0 0
/dev/hdb5 /media/hdb5 ntfs-fuse auto,gid=1002,umask=0002 0 0
/dev/hdb6 /media/hdb6 ntfs-fuse auto,gid=1002,umask=0002 0 0
/dev/hdb7 /media/hdb7 ntfs-fuse auto,gid=1002,umask=0002 0 0
root@r43264r32hf4236:/home/vicho# 

> root@r43264r32hf4236:/home/vicho# sudo fdisk - l

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
root@r43264r32hf4236:/home/vicho#

[http://gnome-look.org/content/show.php/Kore+Suite?content=54701](http://gnome-look.org/content/show.php/Kore+Suite?content=54701)

---

### Post by AlexenderReez on 2007-08-04
please see my link:)

---

### Post by cursebg on 2007-08-04
> **AlexenderReez said:**
> you need to install ntfs-config ...refer this please --->




[B]
UAResolved[/B]
I hope it works, thanks!:)

---

### Post by Inxsible on 2007-08-04
from your fstab, i see that you are trying to mount hdb5 hdb6 and hdb7 at 3 different mount points. one with captive-ntfs one with just ntfs and one with ntfs-fuse. maybe thats the problem. try it like alexander's link.

EDIT : Oh and thanks for the link  to the theme!!

---

### Post by cursebg on 2007-08-04
I followed the steps, then a window poped up, it asked me to choose something about writing and in/ex -ternal things, i chose them both, then i cklicked OK and got this > root@r43264r32hf4236:/home/vicho# gksu ntfs-config

** (ntfs-config:8994): WARNING **: Can't find device with uuid = 468A-8087


** (ntfs-config:8994): WARNING **: Can't find device with uuid = 8D15-011A


** (ntfs-config:8994): WARNING **: Can't find device with uuid = D39F-81B9


** (ntfs-config:8994): WARNING **: Mounting /media/hdb5 failed.

Failed to access '/dev/disk/by-uuid/468A-8087': No such file or directory



** (ntfs-config:8994): WARNING **: Mounting /media/hdb6 failed.

Failed to access '/dev/disk/by-uuid/8D15-011A': No such file or directory



** (ntfs-config:8994): WARNING **: Mounting /media/hdb7 failed.

Failed to access '/dev/disk/by-uuid/D39F-81B9': No such file or directory


root@r43264r32hf4236:/home/vicho# 


---

### Post by cursebg on 2007-08-04
And does it matter that this 'uuid's on my first drive are long and the second drive ones are 8 symbols with a slash in the middle?

---

### Post by AlexenderReez on 2007-08-04
try to reboot see whether the system can detect it or not..if not..then you need to manually mount--->

warning(if you want to follow next guide,please disable and remove ntfs-config first)
attachment :-->

---

### Post by cursebg on 2007-08-04
It doesn't work again ;(

Did I do something wrong :confused: Three days ago I just clicked twice on each partition and it worked! maybe it's a package, or something... 

OK, let's try the manual thing... :) Honestly, I don't have any idea how to disable ntfs-config :D

---

### Post by cursebg on 2007-08-04
[Advertisement] You need to disable a program? You don't know how to? 
Then this is the tool for you! 

Synaptic + Complete Removal!

[/Advertisement]
OK, now could someone tell me what does the error message on the screenshot mean, please?

---

### Post by belikralj on 2007-08-04
Judging by the error message I think you could try ```
sudo nautilus
``` and then try doing what ever you tried to do in the first place. It gives administrative capabilities to what ever you want to do in the 'explorer' :). It could work but this (if it works) would be a temporary fix and you would need to change your ```
/etc/fstab
``` file to make it permanent. Since I don't have the page in front of me any more I'll just have another look and post again.

---

### Post by cursebg on 2007-08-05
OK, so i tried "sudo nautilus" but when i entered in my computer it looked like the attached screenshot.

Here is my /etc/fstab file, please someone hel me fix it :(

```

root@r43264r32hf4236:/home/vicho# cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/hdb1
UUID=78eb77e9-786f-4f54-848a-9effa6ec7a75 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda1
UUID=AA24AD6B24AD3AE9 /media/hda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/hda5
UUID=B87045F67045BBBE /media/hda5 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/hdb5
UUID=468A-8087 /media/hdb5 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/hdb6
UUID=8D15-011A /media/hdb6 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/hdb7
UUID=D39F-81B9 /media/hdb7 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/hdb2
UUID=69797447-7570-4198-9a1d-bddbd5d9010f none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdd /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
/dev/hdb5 /mnt/captive-noname captive-ntfs defaults,noauto 0 0
/dev/hdb6 /mnt/captive-noname2 captive-ntfs defaults,noauto 0 0
/dev/hda5 /mnt/captive-noname3 captive-ntfs defaults,noauto 0 0
/dev/hdb7 /mnt/captive-noname4 captive-ntfs defaults,noauto 0 0
/dev/hda1 /mnt/captive-noname5 captive-ntfs defaults,noauto 0 0
/dev/hdb5 /media/hdb5 ntfs-fuse auto,gid=1002,umask=0002 0 0
/dev/hdb6 /media/hdb6 ntfs-fuse auto,gid=1002,umask=0002 0 0
/dev/hdb7 /media/hdb7 ntfs-fuse auto,gid=1002,umask=0002 0 0
root@r43264r32hf4236:/home/vicho# 
```

---

