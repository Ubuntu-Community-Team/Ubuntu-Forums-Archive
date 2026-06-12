---
title: "fstab &amp; second HD (sdb1)- Ubuntu Dapper"
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by ColinG on 2006-08-29
I've just set up Dapper 64 bit. My Windows partition has been deleted and is now an ext3 linux partition. During the install it has not been picked up. I can mount the drive via "System > Administration > Discs" but any changes there are temporary and have no impact on fstab - I enable the drive and all is well and I get rw access but only until next reboot.

I have tried to mount the drive at /mnt/data but nothing happens. My fstab is below and the drive is sdb1. What do I need to do to get rw access at user level at boot?

Many thanks:) 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sdb1	/mnt/data	ext3	defaults	0	1

---

### Post by TFX360 on 2006-08-29
> **ColinG said:**
> I've just set up Dapper 64 bit. My Windows partition has been deleted and is now an ext3 linux partition. During the install it has not been picked up. I can mount the drive via "System > Administration > Discs" but any changes there are temporary and have no impact on fstab - I enable the drive and all is well and I get rw access but only until next reboot.

I have tried to mount the drive at /mnt/data but nothing happens. My fstab is below and the drive is sdb1. What do I need to do to get rw access at user level at boot?

Many thanks:) 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sdb1	/mnt/data	ext3	defaults	0	1


Dear ColinG,


Backup your fstab first!
```

cp /etc/fstab /etc/fstab.bck
```

```
/dev/sda4       /data           ext3            defaults                        0       0
```

Is a line from my fstab. Edit it where necessary and create a mount point (like /data in your root dir).

The mount point must pre-exist!

then do a

```
mount -all
```

And your ready to go!


The last number in this case 0 is the <pass> change this to 1 to get a fsck every standard 30 boots. Root has this also, depends on how important you think your data on that partition/drive is.

Kind regards,


TFX

---

### Post by ColinG on 2006-08-29
Excellent stuff.

Thanks TFX:D

---

### Post by TFX360 on 2006-08-29
> **ColinG said:**
> Excellent stuff.

Thanks TFX:D

Your quite welcome. I'm quite new to linux. Have been using it for about two to three months.


See ya around,


Kind regards,


TFX

---

### Post by ColinG on 2006-09-01
Oops, I spoke too soon. This is what I did:
sudo mkdir /data
amended fstab as per your illustration
sudo mount -all

I can access the drive and if I open an existing folder on the drive I can write to it (set up a new folder within it for instance).

What I cannot do is access the drive and create a new folder - I'm told "Access Denied".

What am I missing? It must be something to do with permissions.

Thanks
Colin

---

### Post by TFX360 on 2006-09-01
> **ColinG said:**
> Oops, I spoke too soon. This is what I did:
sudo mkdir /data
amended fstab as per your illustration
sudo mount -all

I can access the drive and if I open an existing folder on the drive I can write to it (set up a new folder within it for instance).

What I cannot do is access the drive and create a new folder - I'm told "Access Denied".

What am I missing? It must be something to do with permissions.

Thanks
Colin


Nope, windows isn't open source. As you should well know. NTFS is not supported. You can mount a drive, but you can't write to it. You can however install ntfs-3g via this [how-to]("http://www.ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-3g"). I wasn't up for it as it sounded to buggy.

---

### Post by Bagnaj97 on 2006-09-01
if the partition is ext3 you can just change the owner and group of the folder you mounted it to. If I use /data as an example then you  would do ```
sudo chown yourUsername /data && sudo chgrp yourUsername /data
```

---

### Post by TFX360 on 2006-09-01
> **Bagnaj97 said:**
> if the partition is ext3 you can just change the owner and group of the folder you mounted it to. If I use /data as an example then you  would do ```
sudo chown yourUsername /data && sudo chgrp yourUsername /data
```

Tehee I'm answering to many posts, offcourse you're right!


Shouldn't ```
sudo chown yourUsername /data && sudo chgrp yourUsername /data
``` be

```
sudo chown **-R** yourUsername /data && sudo chgrp yourUsername /data
```

to include subfolders etc.

---

### Post by Bagnaj97 on 2006-09-01
Actually it should be

```
sudo chown **-R** yourUsername /data && sudo chgrp **-R** yourUsername /data
```

Silly me :-(

---

### Post by TFX360 on 2006-09-01
> **Bagnaj97 said:**
> Actually it should be

```
sudo chown **-R** yourUsername /data && sudo chgrp **-R** yourUsername /data
```

Silly me :-(


To err is human. And Ubuntu is for Human Beings! :D

---

