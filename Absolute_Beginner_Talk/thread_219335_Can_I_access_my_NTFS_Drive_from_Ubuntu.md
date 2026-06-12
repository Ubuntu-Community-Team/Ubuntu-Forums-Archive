---
title: "Can I access my NTFS Drive from Ubuntu?"
date: 2006-07-19
forum: Absolute Beginner Talk
---

### Post by fatsheep on 2006-07-19
Title says it all, I am running a dual boot with Ubuntu and Windows XP and I would like to access my XP partition from Ubuntu but I don't know if it is even possible.

---

### Post by Kurt` on 2006-07-19
It should be already mounted in /media. (as read-only)

# ls /media

---

### Post by aysiu on 2006-07-19
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by codejunkie on 2006-07-19
> **fatsheep said:**
> Title says it all, I am running a dual boot with Ubuntu and Windows XP and I would like to access my XP partition from Ubuntu but I don't know if it is even possible.
yes and now with ntfs-3g there is stable read and write NTFS supprot under linux.

---

### Post by fatsheep on 2006-07-19
Having some problems...  Here's my NTFS Drive information:

> **/dev/hdc1   *           1        3712    29816608+   7  HPFS/NTFS**

The guide said I should unmount the partition if I have it mounted already.  I'm not sure if it is or not so I tried to do it:

> 
fatsheep@fatsheep:~$ sudo unmount /dev/hdc1
**sudo: unmount: command not found**


Here's my fstab file:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdc2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


Notice there is no NTFS or hdc1 line.  So I added a line for it:

> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
**/dev/hdc1 /windows ntfs nls=utf8, unmask=0222            0      0**
/dev/hdc2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


I saved the file and followed the mount instructions:

> 
fatsheep@fatsheep:~$ sudo mount -a
**[mntent]: line 5 in /etc/fstab is bad**


Line 5 is the line I added.  

I have tried rebooting and accessing the NTFS partition but I am met with this error:

> 
[mntent]: line 5 in /etc/fstab is bad

mount: can't find /dev/hdc1 in /etc/fstab or /etc/mtab


:confused:

---

### Post by aysiu on 2006-07-19
The command you want is ```
umount
``` instead of ```
unmount
``` Likewise, the /etc/fstab line you want is ```
/dev/hdc1 /windows ntfs nls=utf8,umask=0222 0 0
``` instead of ```
/dev/hdc1 /windows ntfs nls=utf8, unmask=0222 0 0
```

---

### Post by fatsheep on 2006-07-19
Thanks a bunch!  Everything's working great now.  \\:D/

---

### Post by fatsheep on 2006-07-20
And just after I say that the NTFS drive disappears from the "Computer" menu.  Any ideas on getting it back?

---

### Post by OU812 on 2006-07-20
Open the terminal. At prompt enter

sudo mkdir /windows

When you reboot, all should be ok.

john

---

