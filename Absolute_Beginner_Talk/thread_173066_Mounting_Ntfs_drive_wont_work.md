---
title: "Mounting Ntfs drive wont work?"
date: 2006-05-09
forum: Absolute Beginner Talk
---

### Post by aktiwers on 2006-05-09
Hi,

I have posted about this problem before, and dont seam to be able to get it solved.
[http://www.ubuntuforums.org/showthread.php?t=163070&highlight=Remounting+Ntfs]("http://www.ubuntuforums.org/showthread.php?t=163070&highlight=Remounting+Ntfs")

So I will try one more time :)

Can this have anything to do with the fact that im using a new kernel?
Im using this one: 2.6.16-ck3

Okey, to mount my sdb5 ntfs drive I do this:

```

sudo mkdir /media/wd250
sudo mount /dev/sdb5 /media/wd50 -t ntfs -o nls=utf8,umask=0222
``` 
That didnt work, nothing happends. When I go to /media/wd250  the folder is just empty.

So I do this:
```

sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab 
``` 
And ad this to my fstab:
/dev/sdb5       /media/wd250  ntfs    nls=utf8,umask=0222 0       0

Again nothing happends. Then I try this:

```
aktiwers@ubuntu:~$ sudo mount -a
Password:
**mount: /dev/sdb5 already mounted or /media/wd250 busy**

``` 
Why do I keep getting this error?

This is what my fstab looks like:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /media/sda1     ext3    defaults        0       2
/dev/sda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sdc        /media/usb0     auto    rw,user,noauto  0       0
/dev/sdb5       /media/wd250  /dev/sdb5       /media/wd250  ntfs    nls=utf8,umask=0222 0       0 
I have also rebooted. 
Still not working? ](*,)

What am I doing wrong? Back when I was running the old kernel I could mount this drive easy.

Sorry for this long threat, and thanks a lot for reading this fare!
Any one can spot what I am doing wrong?

---

### Post by skippy81 on 2006-05-09
Im not an expert in this area i'm afraid but I do have a suggestion you could try.  I know that ubuntu uses something called EVMS to manage the volumes on your disks.  There is a kernel patch which can be downloaded via a package manager - I believe it is called kernel-patch-evms.  Inside the archive file you will find a patch called evms-bd-claim.  It can be applied to the kernel source in exactly the same way as the CK3 patch was, you would then have to recompile the kernel.  

When I did this it removed a lot of error messeges I was getting at bootup.  Maybe you could check your dmesg and see if you are getting a lot of device-mapper errors.  If you are then it may be worth you trying the evms patch out.

---

### Post by aktiwers on 2006-05-09
Thanks a lot for you reply!
I will try this tomorrow (its late here)

Other suggestions are still very appriciated!

Again thanks a lot :)

---

