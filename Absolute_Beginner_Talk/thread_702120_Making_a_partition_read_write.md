---
title: "Making a partition read write"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by Dakillakan on 2008-02-20
I just partitioned a 100gb section of my hard drive into /dev/sda5 ext2.  When I try change anything within it /media/disk I can not.  It seems that I have "access files only" permission and the root has control. How do I fix this so I can make folders and create files and the such?

---

### Post by brettg on 2008-02-20
Assuming you are mounting the drive in fstab as rw then you are looking at a file permissions problem.

If your user is the only person that needs to write to the file you can simply assign yourself ownership of the by using sudo chown username:usergroup /directory

eg:

sudo chown brettg:brettg /media/sda1/files

---

### Post by spiderbatdad on 2008-02-20
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by ruy_lopez on 2008-02-20
Sometimes when you mount, because mount needs sudo, it changes the ownership of the mountpoint to root. Running "chown yourname:yourname" on the mountpoint usually fixes it, like brettg says.

---

