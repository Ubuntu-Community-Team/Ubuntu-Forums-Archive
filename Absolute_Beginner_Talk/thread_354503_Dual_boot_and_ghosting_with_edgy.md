---
title: "Dual boot and ghosting with edgy"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by ssscccoottt on 2007-02-06
Hi,
I was wondering if it is possible or logical or just a waste of my time to make a dual Edgy boot. :confused: 

I set my hard drive up like so:

```
Edgy installation #1
/dev/hdc3  # /boot  <-- shared by both edgy installs - would this be necessary?
/dev/hdc4  # swap  <-- shared by both edgy installs
/dev/hdc5  # /  <-- working install for everyday usage
/dev/hdc6  # /home  <-- working install for everyday usage

Edgy installation #2
/dev/hdc3  # /boot  <-- shared by both edgy installs - would this be necessary?
/dev/hdc4  # swap  <-- shared by both edgy installs
/dev/hdc7  # /  <-- edgy install used for ghost image
/dev/hdc8  # /home <-- edgy install used for ghost image
```

*i have WinXP booting too, but i'm not mounting it on either.  its on /dev/hdc2

The reason for installing two edgy systems side-by-side is that the 2nd install would be used for ghosting/backup purposes.  Both installs would start off identical, the first installation used for everyday usage and trying out new programs and mucking up the system; the second for my "ideal" system where things in the first install that I liked or worked well would end up.

I could then use partimage to backup the 2nd install (/dev/hdc7 & /dev/hdc8) and restore to the first install.  I'm guessing this part is like using ghosting, but I've never done that before.

When I tried this setup, I did edgy installation #2 first followed by #1.  Install #2 went fine, but when installing #1 and setting up my mounts, I got the message "No root file system."

Should I do away with the /boot partition?  I'm not sure what having that does, because one /boot partition (edgy install #2) would be overwritten by the other (edgy install #1).  

If this is not possible, what other suggestions do you guys have?  I've used partimage to create/restore partitions successfully before, but I guess that I'd like to have a "working" image.

The most recent thing I tried was using partimage to backup my first install and restore it to my second install.  /dev/hdc5,hdc7 are the same size and are /dev/hdc6,hdc8.  My grub only listed the first install.  I'm sure I would have to edit this.  How would I go about doing that?

Whoever reads this, thanks. I know this was long, but I tried to give you all as much detail as possible.  I've solved many a problem with Ubuntu using all of your help!

Scott

---

### Post by Scarlett on 2007-02-06
I would think it's a bit of an overkill to have two partitions.  As long as you can still boot into Ubuntu, a .tar  will do just fine.  This is an easy to follow howto to save your whole system.  

[http://ubuntuforums.org/showthread.php?t=81311](http://ubuntuforums.org/showthread.php?t=81311)

---

