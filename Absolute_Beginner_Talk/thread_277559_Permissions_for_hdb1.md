---
title: "Permissions for hdb1"
date: 2006-10-14
forum: Absolute Beginner Talk
---

### Post by Grundair on 2006-10-14
Evening folks. I am so new to linux that it is well apparent!! But short hereis the  story. I had Kubuntu on a 20 gig maxtor IDE I found an 80 gig maxtor for free. A friend set up my puter origianlly and placed my home files on the 40 gig hdb1. I reinstalled the OS on the new drive  to learn how to do it. I want to use that drive for just media storage, but I can only read it but not write to it.When I try to write to it it says. only root can modify contents.  How do I change permission from root to all users read and write.

Here is the drive listing from my /etc fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
/dev/hdd1 / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0
 1
/dev/hdd5 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/hda1 /windows ntfs nls=utf8,umask=0222,uid=0,gid=0,auto,ro,nouser 0 0

/dev/hdb1 /hdb1 ext2 users,atime,auto,rw,dev,exec,suid 0 0


OR better yet how do I format it and then assign read/write status?

Thanks. This is a great forum and well set up.

CHuck

---

### Post by aysiu on 2006-10-14
Try this: [http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by Grundair on 2006-10-14
Thanks reformated and made it r/w for myself. Just need to figure out how to make it r/w for a 6 of my family. Great help

Chuck

---

### Post by Grundair on 2006-10-16
Thought I would toss out a quick THANKS to aysiu for the help I got. Got the new drive up and runing  everyone has     permissions to read and write and I got a secure folder for each memebr to  store there stuff in.

Chuck

---

### Post by aysiu on 2006-10-16
That's great, Grundair. I didn't really do much besides post a link. Glad it worked out for you, though.

---

