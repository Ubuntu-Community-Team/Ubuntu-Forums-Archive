---
title: "HOWTO: Let Amarok access media on HFS+ partition"
date: 2009-06-11
forum: Apple Hardware Users
---

### Post by rockfloyd on 2009-06-11
My setup is a MacBook Pro 4,1 with Ubuntu 8.10.  What I've been working on is having my Ubuntu partition access my music collection, which is located on my Mac partition.  By default, most of the data on the Mac partition is locked.  After unsuccessfully trying to have the Mac partition automount as root, I attacked the problem from the other side and created a launcher with this command

> gksudo amarok

in the "Command" field.


I hope this can help someone!

---

### Post by cyberdork33 on 2009-06-11
It is really not recommended that you run your applications as root. This is a big a security risk. If you would like to share your OSX user's files with other users, you should modify the permissions on those files to allow access outside the owner.

---

### Post by dmizer on 2009-06-11
Here's the safe way -

Step one:
```
sudo aptitude install hfsplus
```
Step two:
Access drive.

You can also mount the drive with /etc/fstab like so:
```
/dev/<device> /media/mountpoint hfsplus rw,exec,auto,users 0 0 
```

Some sources indicate that you'll have to disable journaling in order to get write access. YMMV.

---

### Post by rockfloyd on 2009-06-12
well, thanks for the responses. good to know that there's a better way of doing it.

---

