---
title: "fstab worries ..."
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by Blofeld on 2007-04-29
One partition gets mounted to /media/disk, I would like to mount it to /media/puppy instead.
I added the folder and edited fstab (using its /dev/hda5 device file) but Xubuntu halted citing a failed fsck before the X server started.
So how do I change the mountpoint to /media/puppy?
BTW, how do I find out a partition's UUID?:confused: 
Thanks!

---

### Post by amaroKer on 2007-04-30
You don't need to worry about uuid.  Just use the /dev/... path as I have shown.  
Here is a copy of my fstab.  Maybe it will help.
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       		<dump>  <pass>
proc            /proc           proc    defaults        		0       0

/dev/sda4	/		ext3	defaults,errors=remount-ro	0	1

/dev/sda3	/misery 	vfat    defaults,utf8,umask=007,gid=46	0       1

/dev/sda5	none		swap    sw              		0       0

/dev/sda6	/home		ext3	nodev,nosuid			0	2

/dev/cdrom	/media/cdrom0   udf,iso9660 user,noauto			0       0
```

---

### Post by PriceChild on 2007-04-30
The uuids may be found in /dev/disk/by-uuid/

I strongly suggest that you keep the UUIDs as it will REALLY help with upgrades to gutsy etc.

If I were you I would just boot up a live cd to change the offending file.

---

### Post by Blofeld on 2007-04-30
@amaroker:  thanks, but I have tried that and it lead to the described problems (although I don't understand why).
@PriceChild:  get in, it worked!  What I did was go to /dev/disk/by-uuid, right click on the files, and then identify them by checking out which file they're linked to.  I then identified the drive I wanted to mount, entered it in fstab, and hey presto!
:guitar:

---

### Post by amaroKer on 2007-04-30
Sorry about that.  I thought I'd read that the UUIDs were inconsequential.  My bad.

---

