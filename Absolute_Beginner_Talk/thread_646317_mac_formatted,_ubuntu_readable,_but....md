---
title: "mac formatted, ubuntu readable, but..."
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by missed her show on 2007-12-21
i've got an external hd.  the main goal is to be able to transfer data from my ubuntu box to my mac laptop via the external hd. 

I've formatted the external hd on the mac.   Ubuntu recognizes, but the disk is read only. 

How can i change the permissions to allow me to copy and write as well? 

thanx in advance

---

### Post by Xiong Chiamiov on 2007-12-21
I'm assuming you're mounting this automatically?
You need to edit your fstab (/etc/fstab).
run
> 
sudo gedit /etc/fstab
 with kwrite instead of gedit for kubuntu.
You need to find your external hd.  If it's mounted at /external, then you'll see a line that says something like
> 
UUID=b4ab24a3-ba8f-4300-a274-afbb90d8d17f /external           ext3    defaults        0       2

In the 4th column, add in umask=000 (in this case, it's after defaults, so it looks like defaults,umask=000 ).  Make sure to note that it's *umask*, not *unmask*.  That cause d me a lot of hearache.

---

### Post by missed her show on 2007-12-21
here's my fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=586ff6b3-b74d-4f2f-a926-617beb0d20be /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=9E283F7E283F548D /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda6
UUID=420e1625-0f3f-4966-b3c2-ec23047fab8a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
```

system monitor tells me that my external hdd is /dev/sdd2 (hfsplus formatted....would that make a difference?)

---

### Post by Xiong Chiamiov on 2007-12-21
Well, let's try putting this at the end of your fstab:
```

/dev/sdd2    /external    auto     defaults,umask=000   0   0

```
with /external being wherever you want it.  Also, if it doesn't mount correctly, try putting hfsplus instead of auto.

---

