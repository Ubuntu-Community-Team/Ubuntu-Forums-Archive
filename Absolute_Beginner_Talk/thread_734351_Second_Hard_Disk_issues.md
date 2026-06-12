---
title: "Second Hard Disk issues"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by mistux on 2008-03-24
Well I don't think I have everything just right, but I think I am close.

My new second hard disk works and I have copied over about 30 gig of files to it, but In order to use it and before my Gallery2 photo site can use it, I have to double click on it in the "Computer--File Browser" then I have to give it my password becasue it comes up with:  ```
Access to this internal disk is restricted to system administrators for security reasons. 
```

I did try to make an entry in the ftab of:
```
/dev/sdb1 	/media/Disk	ext2	defaults	0	1
```
But that did not seem to do anything.

What did I do wrong?

---

### Post by Sam Lars on 2008-03-24
Did you restart or do a sudo mount after you changed the fstab?

---

### Post by mistux on 2008-03-25
Yes, I did a restart after changing the fstab file.

---

### Post by kpkeerthi on 2008-03-25
Can you just do 
```
sudo mount -a
``` in a terminal and post back error, if any?

---

### Post by jken146 on 2008-03-25
If I were you, I would choose a different mount point than /media/Disk, as this is the default place where thigs are auto-mounted.  I'm not sure if it really matters.

Also, the last option should be 2 (not 1 -- 1 is for /).

---

