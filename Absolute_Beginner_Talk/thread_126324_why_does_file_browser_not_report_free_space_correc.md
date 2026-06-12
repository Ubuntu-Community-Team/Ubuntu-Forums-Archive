---
title: "why does file browser not report free space correctly"
date: 2006-02-06
forum: Absolute Beginner Talk
---

### Post by Bubba Ho-Tep on 2006-02-06
I've just spent the last hour pissing about trying to mount 2 hard drives to /mnt

I was judging the results by the free space reported in the File Browser in breezy.

I mount one 80Gb drive on /mnt - this showed up ok. i mount another 80gb - this one doesn't ie File Browser still reports free space at /mnt as 80Gbs even tho I have mounted x2 80Gbs

I've now discovered that mount is reporting both drives _are_ mounted - so why is File Browser getting it wrong?

---

### Post by carlosqueso on 2006-02-06
I believe you can't mount both drives to the same mount point and be able to access them both.  YOu probably need to unmount them both, create two subdirectories for them (/mnt/drive1, /mnt/drive2) and mount them to those.  Then you'll be able to see the free space on both.

---

### Post by BenTyreman on 2006-02-06
If I have read correctly, you are mounting both drives to /mnt. You cannot mount two drives to the same folder; the second mount will just take priority over the first.

You need to mount one to /mnt/hda1 and one to /mnt/hdb1 (or whatever you want to call each subfolder).

The alternative would be to use LVM (Logical Volume Management), which would allow the two hard drives to appear as one (logical) 160GB drive.

---

### Post by Bubba Ho-Tep on 2006-02-07
Aaaaaaaaaaaa, that would explain why (slaps hand on forehead)

I'm actually trying to set up LVM (thought you had to mount the drives first) which isn't going well - but that's a whole 'nother thread.

---

