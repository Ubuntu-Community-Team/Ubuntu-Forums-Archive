---
title: "Remounting Ntfs?"
date: 2006-04-20
forum: Absolute Beginner Talk
---

### Post by aktiwers on 2006-04-20
Hi, 

After installing a new Kernel, my 250gb hardisc is not mounted anymore.
I followed this guide.
[http://ubuntuforums.org/showthread.php?t=157560](http://ubuntuforums.org/showthread.php?t=157560)

and everything is working fine.

But when I try to mount the hardrive again it says:
> aktiwers@ubuntu:~$ sudo mount /dev/sdb5 /media/wd250/ -t ntfs -o nls=utf8,umask=0222
mount: /dev/sdb5 already mounted or /media/wd250/ busy
aktiwers@ubuntu:~$


My Fstab looks like this:

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
/dev/sdb5       /media/wd250  ntfs    nls=utf8,umask=0222 0       0


I have tried to remove the "/dev/sdb5       /media/wd250  ntfs    nls=utf8,umask=0222 0       0" and delete the folder in /Media/ called wd250.

I have also runned the 
```
sudo umount /media/wd250
``` 
And
```
sudo umount /dev/sdb5
```

and started all over. 

```
sudo mkdir /media/wd250
sudo mount /dev/sdb5 /media/wd250/ -t ntfs -o nls=utf8,umask=0222
```

And again started all over and done this:

```
sudo mkdir /media/wd250
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab
```

and added this line to Fstab:
/dev/sdb5       /media/wd250  ntfs    nls=utf8,umask=0222 0       0

But still without luck. 

Anyone has any idea whats wrong here? 
And how I can mount my Ntfs Hardisc again?

---

### Post by Mustard on 2006-04-20
One quick suggestion for when you umount and it gives a 'busy' error.  Try using it with the -l option..

```
sudo umount /media/wd250 -l
```

This should force the umounting of the partition from the mount point.

Check out the option in 'man mount' for detailed explanation.

[quote=man mount]
**-l** Lazy unmount. Detach the filesystem from the filesystem  hierar&#8208;chy now, and cleanup all references to the filesystem as soon as it is not busy anymore.  (Requires kernel 2.4.11 or later.)
[/quote]

---

### Post by aktiwers on 2006-04-30
Thanks for your reply!
I still get the same error? Any other ideas?

---

### Post by Mustard on 2006-04-30
What is the output of these two commands...

```
mount
```

and

```
sudo fdisk -l
```

---

### Post by aktiwers on 2006-04-30
[quote=Mustard]What is the output of these two commands...

```
mount
``` 
and

```
sudo fdisk -l
```[/quote] 
Here is the mount output:

> aktiwers@ubuntu:~$ mount
/dev/sda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
/dev/sda1 on /media/sda1 type ext3 (rw)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)
none on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
aktiwers@ubuntu:~$


 
and the sudo fdisk -l

> aktiwers@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            3409       19929   132704932+  83  Linux
/dev/sda2             126        3408    26370697+  83  Linux
/dev/sda3               1         125     1004031    5  Extended
/dev/sda5               1         125     1003999+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2       30401   244188000    f  W95 Ext'd (LBA)
/dev/sdb5               2       30401   244187968+   7  HPFS/NTFS
aktiwers@ubuntu:~$
 
Anything strange here? 
Thanks alot for your help so fare :)

---

### Post by Mustard on 2006-05-02
Well its not showing it as being mounted from the output of the mount command, so I'm not sure why its returning errors that are saying it's already mounted, as its not.  It could be busy, but I can't see how it is busy when its not mounted.

Can you show us the contents of your /etc/fstab file again?  The only thing I can think of is its a typo or syntax error of some kind in the fstab file.

---

### Post by aktiwers on 2006-05-03
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


Here it is again. Thanks!

---

### Post by Mustard on 2006-05-03
Could you edit your /etc/fstab to include the line in bold below...
(I'm assuming you still have a directory called wd250 in your /media/ directory.)

```

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/sda2 / ext3 defaults,errors=remount-ro 0 1
/dev/sda1 /media/sda1 ext3 defaults 0 2
**/dev/sdb5 /media/wd250 ntfs nls=utf8,umask=0222 0 0**

/dev/sda5 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdd /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0

```

Then type this command to mount all entries in the fstab file..

```
sudo mount -a
```

---

