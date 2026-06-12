---
title: "how do i format a disk!?!"
date: 2005-10-10
forum: Absolute Beginner Talk
---

### Post by dgrafix on 2005-10-10
ive created a fat32 partition that i no longer need and want to make it extended 3. i try disabling it and then format but it says exteded3 but if i clode disks manager and go back in its still fat32. Is this a bug in gnome or is there a way of doing it in root term?

---

### Post by Kyral on 2005-10-10
Command line time!

Check this out if you need a primer.
[http://www.ubuntuforums.org/showthread.php?t=73885](http://www.ubuntuforums.org/showthread.php?t=73885)

Now umount the disk by using
```
umount <whatever the mountpoint is>
```

Now if you know the /dev entry of the disk then cool. If not, cat the /etc/fstab and find the /dev entry on the same line as the partitions mount point. Got it? Cool.

Now...

```
sudo mke2fs -j /dev/xxx
```

Where xxx is the /dev entry of the device.

Then just update the fstab to say "ext3" instead of "vfat" and you are done

---

### Post by dgrafix on 2005-10-10
Now im confused. 
 
my fstab reads now like this:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       /media/hdd1     ext3    iocharset=utf8,umask=000        0       0
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/hdd2     ext3    iocharset=utf8,umask=000        0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

Hda1 and 6 are the same disk, 6 is the partition in question
hdc? is my second hard disk (why isnt it hdb1?)

hdd1 now seems to mount ok and i can see it, but 
hdd2 when i choose to mount says this:

mount: /dev/hdc already mounted or /media/hdd2 busy
but nothings using it??? and its not mounted (that i casn see)

Now, when i go into system>administration>disks and choose enable (i assume this is mount) it seems to mount ok

Why doesnt the disk manager in gnome reflect fstab?

---

### Post by Kyral on 2005-10-10
I don't know...it should...fstab is the tried and true way to way to mount stuff.

If its working now ignore the next section or you may want to anyway so we can get this thing in fstab. 

Do this in a terminal while the disc is "enabled"

```
df -T
``` 
and paste the output

---

### Post by dgrafix on 2005-10-11
It all seems to be working as i expect now, but waht does volatile mean in the following (sounds bad!)

Filesystem    Type   1K-blocks      Used Available Use% Mounted on
/dev/hda1     ext3    19607924   5955260  12656636  32% /
tmpfs        tmpfs      112236         0    112236   0% /dev/shm
tmpfs        tmpfs      112236     12588     99648  12% /lib/modules/2.6.12-9-386/volatile
/dev/hda6     ext3    19607892   2454604  16157264  14% /media/hdd1
/dev/hdc1     ext3    18492940   1367844  16185700   8% /media/hdd2

BTW, What is the lost and found dir for?

---

### Post by Kyral on 2005-10-11
Ooops. I should have added the -h option.

Try

```
df -hT
```

that should fix it. Paste please :D

Lost+Found appears on every partition. I think that if during fsck it picks up like orphaned data it puts it there

---

### Post by dgrafix on 2005-10-11
dont panic, its ok now :) thanks

---

