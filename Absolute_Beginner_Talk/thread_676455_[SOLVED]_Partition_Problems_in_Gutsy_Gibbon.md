---
title: "[SOLVED] Partition Problems in Gutsy Gibbon"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by Jeezus on 2008-01-23
WHen I installed ubuntu, I set it up with 3 partitions on my HD. One for the system, one for swap, and one for storage... I called "media".
I can't quite figure out how to access my media partition. It keeps telling me that I don't have permission to copy files to it, and what have you. how do I fix this?

---

### Post by Arthur Archnix on 2008-01-23
Depends on where you mounted this media partition. Output of ```
cat /etc/fstab
``` will show you where it's mounted. Let's say it's mounted at /mnt/media the way you would take ownership of the directory is with
```
sudo chown -R username:username /mnt/media
```
replacing username, with your own, and /mnt/media with what fstab shows you of course.

---

### Post by Jeezus on 2008-01-23
jeezus@MacWheezy:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=cadcd4c5-5058-42f9-94ea-019762e5d136 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda3
UUID=d279a1ca-9d38-47c2-a583-b5e9650bb6ad /media          ext3    defaults        0       2
# /dev/sda2
UUID=ee22a987-0ca7-440e-b797-df8df1b0ac64 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

I don't quite understand this...
It's mounted at just "/media"? right?

---

### Post by Arthur Archnix on 2008-01-23
Yeah.. which *may be* bad idea because that tends to be where Ubuntu loads stuff that's automounted. I'm not certain, but this could confuse the system. Better off to put it somewhere like /data or /shared, or /mnt/media (though if it goes here it will show up on your desktop). Anyway, I'd change it from this
> # /dev/sda3
UUID=d279a1ca-9d38-47c2-a583-b5e9650bb6ad /media ext3 defaults 0 2
To this:
```
# /dev/sda3
UUID=d279a1ca-9d38-47c2-a583-b5e9650bb6ad** /data** ext3 defaults 0 2
```
Next time you reboot, just do that chown command I gave you above on /data.

Or, if you like just chown /media. I'd recommend mounting somewhere else though.

EDIT. Oh, just realized you may need the command to edit it. :)
```
gksudo gedit /etc/fstab
```

---

### Post by Jeezus on 2008-01-23
I don't seem to be able to access that partition at all now
after changing the name to /data

---

### Post by Arthur Archnix on 2008-01-23
In a terminal, do
```
cd / && ls
```
Do you see /data?

If so, 
```
cd data && ls
```

That will show you what's in there, if anything. 

Or, in nautilus, your file manager, go to file system, right-click on data, and choose properties. How much free space do you see? Should be about the size of the partition. 

Confirm that data is lowercase in both the filemanager and in your fstab. Case matters.

Oh, and post the output of this again:
```
cat fstab
```
Also, this too
```
sudo fdisk -l
```

EDIT: Another way, maybe easier, go to >system >administration >system monitor. Then flip over to the file system tab. You should see your partition and where it's mounted.

---

### Post by Jeezus on 2008-01-23
nope... not there.
I'm just gonna reinstall.
I haven't really done anything yet, and I know how to get this far now without any troubles.
I'm gonna set my data partition to </media/data> 
It'll also clear out a lot of redundant programs and whatnot from not quite understanding what I was installing. ;)

---

### Post by Jeezus on 2008-01-24
Well, a fresh install, with a properly partitioned HD certainly did the trick. ;)
I've got it set up proper now, and I just need to install a few more progs before I'm finished. =)

---

### Post by Arthur Archnix on 2008-01-24
Good to hear.

---

