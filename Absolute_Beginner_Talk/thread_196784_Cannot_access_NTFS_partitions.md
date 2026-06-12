---
title: "Cannot access NTFS partitions"
date: 2006-06-14
forum: Absolute Beginner Talk
---

### Post by mchlor on 2006-06-14
Hi, I've got 2 hd's both formatted with ntfs.  Ubuntu 6.06 mounts all my windows xp ntfs volumn but I cannot access any one of them.

Question 1.  Do I need to be root user b 4 I can access these?  If so how do I become a root user?

Question 2.  I'm not comfortable running linux as root user, is there anyway I can access date on my ntfs partitions as a normal user?

Thanks.

---

### Post by taurus on 2006-06-14
I assume you mount those NTFS drives with /etc/fstab.  In there, add "umask=0222" after the defaults so it would look something like
```

dev/hda1     /mnt/first_windows     default,umaks=0222      0     0

```
You can edit your /etc/fstab by (running from a terminal)
```

sudo gedit /etc/fstab

```
Now, you can read from your NTFS as a regular user...

And no, it is NOT a good idea to run everything as root because one wrong command can damage your whole system.  Just be real careful when you "su -" or sudo...

---

### Post by AndyCooll on 2006-06-14
No you don't have to be root user to access the data, it's all to do with the parameters you set on mounting it.

More information can be found here: [Mount Ntfs On Boot]("https://wiki.ubuntu.com/MountNtfsOnBoot")

:cool:

---

### Post by mchlor on 2006-06-14
My fstab looks like this

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0


and my disks are like this
[img]http://img118.imageshack.us/img118/179/screenshot8nz.jpg[/img]
I wanna access my maxtor, samsung and wdc drives.  They got all my mp3z , jpegs and movies.  thanks.

---

### Post by Sutekh on 2006-06-14
You should read this link and follow the instructions.  It will show you how to mount your Windows partitions, so you can access them

[http://psychocats.net/ubuntu/mountwindows.php](http://psychocats.net/ubuntu/mountwindows.php)

---

