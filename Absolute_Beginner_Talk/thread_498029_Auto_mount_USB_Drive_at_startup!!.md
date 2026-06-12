---
title: "Auto mount USB Drive at startup!!"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by Algoodman on 2007-07-10
**Auto mount USB Drive at startup!!**
We have the MIT open course were USB drive which we wish to share in our network using our web-server which is running Ubuntu 6.10, but we want to mount it in /home/sites/MITocw
At last we are able to mount the drive using the following command written in fstab:
/dev/sdb1 /home/sites/MITocw ntfs rw,suid,auto,nouser,sync o o

this mount the drive even after restart but come the problem which is the first two or three pages will open after which the rest will not but if we use the following command which has to be done manually any time the server is restarted:

sudo mount –t ntfs /dev/sdb1 /home/sites –o umask=0222 –o uid=1028,gid=100

Now every page will open and we can access it over the intranet. Now my question is most I keep on doing this manually? What is the defaults configuration in the auto run all about?

---

### Post by PriceChild on 2007-07-11
*moves and bumps*

---

