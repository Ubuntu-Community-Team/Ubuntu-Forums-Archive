---
title: "loging into ubuntu as root?"
date: 2006-05-03
forum: Absolute Beginner Talk
---

### Post by cptjaben on 2006-05-03
hi, i'm wondering if there is a way to log into ubuntu as root so that i can change these permission on my windows(ntfs) harddrive. 

[IMG]http://img133.imageshack.us/img133/5408/screenshot2ku.png[/IMG]


Thanks,
cptjaben

opps, looks like i spelled logging wrong in the title

---

### Post by aysiu on 2006-05-03
Oh, where to begin.

First of all, NTFS will be read-only at best.
To mount it read-only, follow these directions:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

Secondly, logging in as root isn't necessary.
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by nudnik on 2006-05-03
Unfortunately I have no experience manipulating Windows files via Ubuntu.

To make yourself root in Ubuntu, open a terminal and type : sudo -s

---

### Post by elamericano on 2006-05-03
I'm not sure why Ubuntu mounts with read permissions only for root (it happened to me too) You'll need to add umask=0222 to the appropriate line in fstab. aysiu's link shows it here:

/dev/hda1 /windows ntfs nls=utf8,umask=0222 0 0

I recall that mine didn't work the way I wanted until I added a gid=106 (gdm's group id). Like so:

/dev/hda1 /windows ntfs nls=utf8,umask=0222,gid=106 0 0

Maybe it should have worked without this step. I'll try again when I install Dapper.

---

### Post by cptjaben on 2006-05-03
i changed my /etc/fstab to this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1 	/media/hda1	ntfs 	nls=utf8,umask=0222 	0 	0
/dev/hdb1       /media/hdb1     vfat    iocharset=utf8,umask=000   0       0
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

i'm still have the exact same problem as shown in my orignal post and i'm wondering is there is just a way to log on as root at the login screen and then just change the permissions by checking in the boxes. it seems as though the problem would be easily fixed if i could do this. Thanks for all the help so far.

---

### Post by aysiu on 2006-05-03
Did you reboot or unmount and remount the partition after you changed the /etc/fstab? You have to do that in order for the changes to take effect.

And, no, you can't just check the boxes, even if you gain root privileges. NTFS and FAT32 do not support Linux permissions. They need to be mounted with the correct umask.

---

### Post by cptjaben on 2006-05-03
lol, after restarting my computer everything works fine. Thanks for the help everyone, and please forgive me for my ignorance.

---

### Post by elamericano on 2006-05-04
sudo mount -a

will remount everything in fstab, except for lines with the 'noauto' option.

---

