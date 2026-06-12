---
title: "Disk Usage Question"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by MeanStreak on 2008-01-02
Hi,

I am new to Ubuntu and trying to get my head around file system capacity etc. When I run Disk Usage Analyzer and Scan Home, my Home directory usage is declared as 100% despite my total filesystem capacity being 210.3GB (used 125.1GB available 85.2GB), root (/) also declares 100% usage. 

How can I have 85GB available and yet be using 100% of the space in my root directory.

---

### Post by jken146 on 2008-01-02
What is the output of ```
df -h
```?

---

### Post by MeanStreak on 2008-01-02
Output is as follows:
> 
charles@charles-desktop:~$ df -h
Filesystem            Size Used Avail Use% Mounted on
/dev/sda2              44G   43G     0 100% /
varrun                506M  100K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M   92K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   34M  472M   7% /lib/modules/2.6.22-14-generic/volatile
/dev/sdb1             102G   49G   48G  51% /home
/dev/sda1              66G   35G   32G  53% /media/sda1
overflow              1.0M  376K  648K  37% /tmp
charles@charles-desktop:~$ 


---

### Post by jken146 on 2008-01-02
Well, as you can see it agrees that / is full.  /home appears not to be though.  I've read about this before I think -- try searching the forums.

By the way, if you post in code tags instead of quote tags it'll format much better.

---

### Post by MeanStreak on 2008-01-02
Thanks - I'll partition some more space to /. Just for my information - which drive is designated as root in this terminal response? Sda2?

---

### Post by jken146 on 2008-01-02
Yep -- sda2.

---

### Post by MeanStreak on 2008-01-02
Thanks for that. 

One more quick question - I have 40GB unallocated space in sdb - I would like to add this free space to /home - how do I do this? I have gparted installed.

---

