---
title: "Mounting Partition"
date: 2006-07-30
forum: Absolute Beginner Talk
---

### Post by jd65pl on 2006-07-30
Hi,

I have been trying to mount my old windows partition which I have reformatted to ext3. I am able to mount the drive but not set the read/write settings on the drive.

Please help! Its driving me nuts!

---

### Post by rowanparker on 2006-07-30
So is the partition ext3 or is it NTFS?
How are you mounting it, fstab or the mount command?
Have you got the correct permissions?

---

### Post by Jagot on 2006-07-30
[http://www.psychocats.net/ubuntu/mountlinux.html](http://www.psychocats.net/ubuntu/mountlinux.html)

---

### Post by jd65pl on 2006-07-31
> have reformatted to ext3

I have tried both fstab and mount

I don't seem to be able to set the permissions I have been using sudo

---

### Post by OU812 on 2006-07-31
So you have an entry in your fstab and you mkdir to create a mountpoint? Ok, please post your fstab.

john

---

### Post by jd65pl on 2006-07-31
Here is my fstab it is hda1 I am trying to mount


# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1 	/home/jamie/My_documents	ext3 	defaults 	0 	0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by rowanparker on 2006-08-03
Does it give any errors whilst mouting?

---

### Post by jd65pl on 2006-08-03
Thanks to everyone who has give assistance in this thread, I have decided to re-partition my drives instead.

J

---

