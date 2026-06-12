---
title: "Partition names when installing"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by cygnis1 on 2007-05-08
While going through the partitioning portion of the Ubuntu 7.10 the installer shows the hd partitions as /dev/sda1,2,5, or 6.  But it also shows them as /media/sda1,2,5,or 6.  Does this matter?  I don't want to put Ubuntu where I can't find or use it.
Thanks,
Cygnis1

---

### Post by hyper_ch on 2007-05-08
The /dev contains the actual devices... e.g. harddisks, cd-drive, usb-sticks,....

/media/sda1 .... that's just a place where you actually make the devices availab le in the files system (by mounting them)

---

### Post by kebes on 2007-05-08
The "/dev/sda1" is the "device location". This is assigned by the operating system during boot, and you can't change it. This is how you refer to specific devices.

The "/media/sda1" names are the "mount points". This is where the system is going to "mount" those partitions (i.e.: where the data in those partitions will show up in your filesystem). During installation, you can actually change those names if you want. So instead of mounting the "/dev/sda6" partition at "/media/sda6" you could mount it as "/media/backupdrive", or whatever meaningful name you like.

In fact, you could mount it at "/backup" if you wanted to (putting extra partitions into "/media/" is a good way to keep things organized, but is not mandatory).


During a typical install, you need to define a particular partition as "root", which gets mounted at "/". The other partitions end up being loaded into "/media/" by default, but like I said, this is highly customizable.


Does that answer your question?

---

### Post by cygnis1 on 2007-05-08
Thank you.  This is very helpfull.
Cygnis1

---

