---
title: "Hard Drives not mounting on Startup"
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by rubbsdecvik on 2006-10-12
Ok, so I've kinda tried to find out a little of what i needed, but I'm sort of at a loss as to where to start.

I have three Hard drives in my computer.  Two IDE drives and a SATA drive.  The boot drive obviously mounts and works, it is the first IDE drive on the master.  The SATA drive after a startup ends up mounting to a directory in my /tmp directory.  The second IDE drive doesn't mount anywhere at all.  Using the GUI I change the directories to where I want them to be and enable the drives, but any time I start up the computer I have to do the whole process over again.


Here is the output of my fstab file:
```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       38913   312568641   83  Linux

Disk /dev/hda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9634    77385073+  83  Linux
/dev/hda2            9635       10011     3028252+   5  Extended
/dev/hda5            9635       10011     3028221   82  Linux swap / Solaris

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       19457   156288321    7  HPFS/NTFS

```

thank you in advance for any help I can get!

---

### Post by Kateikyoushi on 2006-10-12
The mount points are missing, basically the whole fstab seems messed up to me.

It looks like an fsidk -l output.

Are you sure that is your fstab ?

```
cat /etc/fstab
```

---

### Post by kidders on 2006-10-12
Hi there,

The stuff you posted isn't from an /etc/fstab ... or at least if it is, it's amazing your system boots at all!

What you *should* have is something like this...

```

/dev/hda1 /boot ext2 noauto 0 0
/dev/hda2 / reiserfs defaults 0 0
/dev/sda1 /home ext3 noexec 0 0
/dev/sdb1 /opt/music reiserfs notail,noatime,noexec 0 0
/dev/hda3 none swap defaults 0 0
...
...

```

Your filesystem mount points will (or should) appear in there.

---

### Post by rubbsdecvik on 2006-10-12
ooopss  your right... sorry posted the wrong stuff... 

Here is my fstab file

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

there we go...
sorry.

---

### Post by Kateikyoushi on 2006-10-12
okay lets backup your existing fstab

```
sudo cp /etc/fstab /etc/fstab_backup
```

Lets create the directories in /media

```
sudo mkdir /media/hdb1
sudo mkdir /media/sda1
```


Edit the fstab

```
gksudo gedit /etc/fstab
```

Add these two lines
```

/dev/hdb1    /media/hdb1 ntfs  nls=utf8,umask=0222 0    0
/dev/sda1    /media/sda1 ext3    defaults,errors=remount-ro 0    1
```

---

### Post by bodhi.zazen on 2006-10-12
You need to add the partitions you want mounted at boot to fstab.

[[color=darkred]How to fstab[/color]](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

### Post by rubbsdecvik on 2006-10-12
Thanks!  I'll try that.  Hopefully it will work.

Thanks again!

---

