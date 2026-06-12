---
title: "FAT32 Owner"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by weaver4 on 2007-07-04
I have a Fat32 partition on my hard drive.  I set this up so that I could get to this partition using both Ubuntu and Windows.

My problem is that I can's seem to change the owner of the drive or folders on the drive so that I can write to this partition in Ubuntu.  I tried loging into nautilus as root but when I set the permissions they won't change.  When I try to set myself as the owner it says "The owner cannot be changed"

I tried to use chmod in the terminal but it says permission is not granted.

So how do I set myself as the owner of this drive.  Or what is the best work around?

---

### Post by bodhi.zazen on 2007-07-04
For a fat partition you set ownership at the time of mounting.

mount /dev/hdxy /mount/point -o uid=<user>,gid=<group>,umask=007

or in fstab

/dev/hdxy mount/point vfat auto,uid=<user>,gid=<group>,umask=007 0 0

---

