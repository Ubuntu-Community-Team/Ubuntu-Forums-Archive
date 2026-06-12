---
title: "view hard drive free space"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by Matt26 on 2008-04-15
is there any easier way to look at the capacity and free space available on all of my hard drive partitions than going into Partition Editor?  something like My Computer in Windows XP where you the information is available by hovering your mouse pointer over a given partition maybe?  thanks.

---

### Post by Inxsible on 2008-04-15
> **Matt26 said:**
> is there any easier way to look at the capacity and free space available on all of my hard drive partitions than going into Partition Editor?  something like My Computer in Windows XP where you the information is available by hovering your mouse pointer over a given partition maybe?  thanks.
1) You can install conky which will display all info about your machine on the desktop all the time. Great app IMHO

2) System>>Preferences>>System Monitor. The filesystem tab will show you all mounted partitions and their usage.

---

### Post by crashcoredump on 2008-04-15
Or 


```
$ df -h


zao@Painhu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             106G  7.6G   93G   8% /
varrun                1.8G  216K  1.8G   1% /var/run
varlock               1.8G     0  1.8G   0% /var/lock
udev                  1.8G   72K  1.8G   1% /dev
devshm                1.8G     0  1.8G   0% /dev/shm
lrm                   1.8G   34M  1.7G   2% /lib/modules/2.6.22-14-generic/volatile
/dev/sdb              917G   89G  783G  11% /media/Storage
zao@Painhu:~$ 

```

---

### Post by Inxsible on 2008-04-15
I was going to mention df -h,,but since I am not on Ubuntu right now (at work on XP :( ) I wasn't 100 % certain whether it also displayed usages :)

Well now I know

---

