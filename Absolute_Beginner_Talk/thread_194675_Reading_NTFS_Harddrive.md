---
title: "Reading NTFS Harddrive"
date: 2006-06-11
forum: Absolute Beginner Talk
---

### Post by goodmore on 2006-06-11
Complete Newbie. How do I read my second harddrive which has a bunch of files I need. It says I don't have permissions. I don't know if the drive is mounted or not. when I right click the drive there is a line that says unmount volume. when I try to do that I get Error: mount point /tmp/disks-conf-hdd1 is not below /media/


Help please. I don't want to reinstall windows to get at this drive.

---

### Post by djsroknrol on 2006-06-11
look at /etc/fstab...

it will tell you if it's mounted or not. The file can also be edited to include your drive at boot up. I believe your second HD would be hdb1. You could just cut and paste in your text editor and change the "a" to a "b".

---

### Post by djsroknrol on 2006-06-11
BTW....you don't want to write to a NTSF system from linux (bad karma :))

---

### Post by aysiu on 2006-06-11
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

