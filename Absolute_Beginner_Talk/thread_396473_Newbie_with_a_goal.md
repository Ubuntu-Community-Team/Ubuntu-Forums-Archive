---
title: "Newbie with a goal"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by jgar on 2007-03-29
I have a rather simple goal.  Create a fileserver for several windows boxes.  I am rather new to linux though i have installed ubuntu successfully.  I know I need to use SAMBA.  However here are my roadblocks.

I don't know how to mount a drive.  (or in particular format my 2tb raid 5 drives)

I am unsure what format would be best for my fileserver so that XP computers can access it.

If you could suggest some reading or ideas to help me reach my goal I would appreciate it.  

Thanks all.

---

### Post by indytim on 2007-03-29
I can answer one of your questions:

> I am unsure what format would be best for my fileserver so that XP computers can access it.

Don't worry about it, use the native ext3.  With the samba mounts to Win they'll see it ok.  Stay away from FAT32 if you're file size is going to exceed >4G. Other wise F32 would be ok also.

As far as source, do a little bit of searching either in the WIKI or on the boards here.  You'll find tons of resource material.

Hope these bits help out.

IndyTim

---

### Post by jgar on 2007-03-29
thanks for your help with the filesystem.

---

