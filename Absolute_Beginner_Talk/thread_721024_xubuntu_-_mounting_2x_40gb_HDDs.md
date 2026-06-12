---
title: "xubuntu - mounting 2x 40gb HDDs"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by madhatter563 on 2008-03-10
I apologize if this is a repeat thread, please just direct me to a thread if you know one that deals with the issue, i could not find one.  

I added 2x 40gb HDDs to an xubuntu machine and only 1 mounted correctly.  I reformatted them both as ntfs in gparted and it was successful.  It looks like the one that wont mount doesnt have a mount point set.  I tried doing things myself but fstab is confusing me.  Any easy way to just re-mount the drives correctly so they both are accessible? Thanks in advance!

---

### Post by BDNiner on 2008-03-10
[https://help.ubuntu.com/community/DrivesAndPartitions](https://help.ubuntu.com/community/DrivesAndPartitions)

This is from the documentation website

---

### Post by madhatter563 on 2008-03-11
alright, thats definitely helpful, but i get stuck when i try:

```

$ sudo mount -a
mount: mount point /media/40x1 does not exist
mount: mount point /media/40x2 does not exist


```

---

### Post by BDNiner on 2008-03-11
you need to create the mount points first

sudo mkdir /media/40X1

---

### Post by madhatter563 on 2008-03-11
thanks, got it working correctly with that command.  I did have to go back and edit fstab again to change the lowercase "x" in 40x1 to upper but then it looked right.  For anyone else having problems, a good way I checked was to add the free disk space checker to the top panel, and set it to that mount point.  I also used "disk space analyzer" to follow up.  Thanks for all the help!

---

### Post by BDNiner on 2008-03-11
You could have used whatever name you liked so long as it is consistent, remember that things are case sensitive. Glad i could help.

---

