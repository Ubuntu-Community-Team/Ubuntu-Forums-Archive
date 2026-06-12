---
title: "Need help migrating to larger hard drives in RAID."
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by bipolardave on 2007-02-16
Hey there.

I recently picked up a Dell PowerEdge 2400 with onboard RAID controller and SCSI drives.

I installed Ubuntu server, GNOME, and even BOINC and the machine is running fine and currently crunching for SETI.

However, now it's time to put it to use as file and print server.  Unfortunately, I installed Ubuntu onto a mirrored 9GB array.  I now have several 18GB SCSI drives and would like to migrate the current setup from the 9GB drives to the 18GB.

Since there's very little on the machine now, I could easily reinstall everything in the course of an afternoon.  But where's the challenge in that?  What I really want to learn is how to migrate the exact disk image (partitions and all) to another, larger array. 

Can anyone help?

Thanks!

---

### Post by laidback on 2007-02-16
On an IDE drive I've copied an image from hdd to hdd with Gparted. Others report success with this using the more advanced drives. I've gone from my working hdd to a usb backup partition then onto another working hdd which was then installed onto a completely different pc. It worked despite differences in mobo, RAM, CPU, video cards etc, brilliant.

Gparted files
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

Documentation
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

---

