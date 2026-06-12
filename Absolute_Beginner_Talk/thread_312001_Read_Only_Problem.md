---
title: "Read Only Problem"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by olopolo on 2006-12-03
Hi. I followed every step for read/write support on this t[opic]("http://www.ubuntuforums.org/showthread.php?t=217009&highlight=mount") but now the ntfs partitions are read only, even access only ? How can I solve it?

---

### Post by taurus on 2006-12-03
Let's have a look at your /etc/fstab!!!

```
cat /etc/fstab
```

---

### Post by atoponce on 2006-12-03
NTFS partitions are only mounted as read-only.  It takes changing a kernel module to get write-access, regardless of how your /etc/fstab is.  At least that's how it was just a couple years ago.  Microsoft isn't releasing the NTFS spec, so write access is limited at best.  I would be interested to know, though, if this is no longer the case.

---

### Post by taurus on 2006-12-03
> **atoponce said:**
> NTFS partitions are only mounted as read-only.  It takes changing a kernel module to get write-access, regardless of how your /etc/fstab is.  At least that's how it was just a couple years ago.  Microsoft isn't releasing the NTFS spec, so write access is limited at best.  I would be interested to know, though, if this is no longer the case.
You can write to it with ntfs-3g!!!

[http://www.ntfs-3g.org/](http://www.ntfs-3g.org/)

---

### Post by atoponce on 2006-12-03
Haven't tried that software before, but it says it's in BETA status.  Is it any good?

---

### Post by taurus on 2006-12-03
Almost half of the stuff that you use is beta and as far as I know, it is working fine for others...

---

### Post by atoponce on 2006-12-03
Good point.  If it is working fine, and doesn't cause any of the headaches that writing to NTFS file systems have been known to cause...

---

### Post by olopolo on 2006-12-04
Sorry for late reply . This is the fstab

[[IMG]http://img292.imageshack.us/img292/200/1im6.th.jpg[/IMG]](http://img292.imageshack.us/my.php?image=1im6.jpg)

---

### Post by taurus on 2006-12-04
> **olopolo said:**
> Sorry for late reply . This is the fstab

[[IMG]http://img292.imageshack.us/img292/200/1im6.th.jpg[/IMG]](http://img292.imageshack.us/my.php?image=1im6.jpg)

How come you have two entries for both /dev/hda1 & /dev/hda5?  You need to edit your /etc/fstab and remove the two entries for /dev/hda1 & /dev/hda5 that have UUID in front!!!

---

### Post by olopolo on 2006-12-06
Thank you @Taurus . I solved the problem. But as we can see in screenshot, some lines are commented in fstab. I am confused how these lines processed by the system?

---

### Post by taurus on 2006-12-06
Lines start with # mean comments and the system won't read them.  So, if you want to add comment or comment something out in /etc/fstab, just put a # in front of it.  (And that goes for /etc/apt/sources.list as well...)  ;)

---

### Post by peterj on 2006-12-06
Hey I have quite a problem, I think better here than a new thread as its quite related. 
Quite simply I made a mess of permissions on everything. I cant mount drives, access admin anything. 
All I want to to is get one really important file of the box and then I'll happily re-install. Can't seem to mount external cdrom or any other usb devices. Just one file!

---

### Post by olopolo on 2006-12-06
> **taurus said:**
> Lines start with # mean comments and the system won't read them.  So, if you want to add comment or comment something out in /etc/fstab, just put a # in front of it.  (And that goes for /etc/apt/sources.list as well...)  ;)

But on this [page]("http://ubuntuforums.org/showpost.php?p=1833363&postcount=1034") the possible solution was given with # for my ex-read only problem.I am confused. I kow comments not processed but why he/she gives the solution with #. Thanks

---

### Post by CatKiller on 2006-12-06
> **olopolo said:**
> But on this [page]("http://ubuntuforums.org/showpost.php?p=1833363&postcount=1034") the possible solution was given with # for my ex-read only problem.I am confused. I kow comments not processed but why he/she gives the solution with #. Thanks

You're confused because you're blind to line breaks :)

There is a commented line of 

```
# /dev/hda1
```

 which, as you say, is ignored, and then the amended line of 

```
UUID=E844661E4465F02C /media/hda1     ntfs-3g    defaults,locale=en_US.utf8 0       1
``` which is followed in its entirety. It's the same for the pair of lines underneath.

---

