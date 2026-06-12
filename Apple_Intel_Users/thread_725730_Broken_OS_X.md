---
title: "Broken OS X"
date: 2008-03-16
forum: Apple Intel Users
---

### Post by Mr. Pink on 2008-03-16
I have a MacBook Santa Rosa that I dual boot OS X and Ubuntu.  I use rEFIt, and haven't been using Linux lately because of touchpad issues (irrelevant to this post).  Anyway tonight after I was done adjusting some controls and themes in Linux I went to boot OS X and it gets stuck at the gray Apple screen for a few minutes and then reboots itself again.  Is this something I did wrong in Linux or do I have bigger issues? 

Also, the Mac side of the harddrive still mounts each time I boot Ubuntu.

---

### Post by cyberdork33 on 2008-03-16
> **Mr. Pink said:**
> Also, the Mac side of the harddrive still mounts each time I boot Ubuntu.
That is likely the issue... remove the offending lines from /etc/fstab and then boot from the restore DVD and run repairs on your OS X partition. (or boot in single user mode [CMD-S] and follow instructions there)

---

### Post by Mr. Pink on 2008-03-16
Ok so there aren't any lines in fstab that mount the drive, but it shows up as "Macintosh HD" in Places when I open nautilus.  I tried to run a verify/repair from the OS X install disk but it failed.  Any ideas where to go from here?  Thanks again.

---

### Post by cyberdork33 on 2008-03-16
> **Mr. Pink said:**
> Ok so there aren't any lines in fstab that mount the drive, but it shows up as "Macintosh HD" in Places when I open nautilus.  I tried to run a verify/repair from the OS X install disk but it failed.  Any ideas where to go from here?  Thanks again.It is not mounted, it is just showing you that it is available. You can double click it to mount it.
I don't know what is wrong with your OS X partition.

---

### Post by sublime on 2008-03-17
Maybe try a permissions repair from the restore disk.

---

### Post by dmitrijledkov on 2008-03-17
I have excatly same problem =D

I think it started after I upgraded to Hardy Alpha 6

---

