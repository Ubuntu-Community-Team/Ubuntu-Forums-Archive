---
title: "Access unrecognized partitions?"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by srusso on 2006-08-25
How do you access unrecognized partitions? I want to refomat an external drive thats not showing on desktop or in System > Administration > Disks

Where can I look otherwize?

---

### Post by bulldog on 2006-08-25
If the external drive is USB then it should be autodetected and visible in your /Media folder.
When it's a firewire drive I'm not sure at all if it's detected by Ubuntu.

But you can try gparted to format your drive in what extension you want.

Be sure to format the right disk [look twice] because it could be a little confusing the first time.

---

### Post by nrwilk on 2006-08-25
Have you mounted the disk?  The disk needs to be mounted in order for you to view it's partitions.

The technical explanation of this is that the disk must have an entry in /etc/fstab.  Usually this can be accomplished very easily in ubuntu by simply double-clicking the disk icon on your desktop after you've plugged it into your USB port.  The icon should have some indication that the disk is mounted.  In KDE you will see a little green triangle in the icon's corner.  I'm not sure how Gnome displays it, or even if it does.


Once the disk has been mounted, you should be able to view and edit its partitions.

---

### Post by nrwilk on 2006-08-25
> **bulldog said:**
> When it's a firewire drive I'm not sure at all if it's detected by Ubuntu.
Yes, firewire drives are definitely detected by ubuntu.  And very well, too.

> **bulldog said:**
>  Be sure to format the right disk [look twice] because it could be a little confusing the first time.

This is excellent advice.  I *HAVE* accidentally formatted the wrong drive before.  That sucked a lot.

---

### Post by bulldog on 2006-08-25
TY for the info about firewire hdd's.

And about formatting the wrong drive.....................I had a bad experience myself,and it aint funny.](*,)

---

### Post by srusso on 2006-08-26
GParted work very good for me...

---

### Post by nrwilk on 2006-08-26
Great!  I'm glad you got it worked out. :)

---

