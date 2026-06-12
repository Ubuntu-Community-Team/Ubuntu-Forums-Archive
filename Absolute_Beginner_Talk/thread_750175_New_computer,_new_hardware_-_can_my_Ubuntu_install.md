---
title: "New computer, new hardware - can my Ubuntu installation still work?"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by JamesDS on 2008-04-09
Hey,

I have recently upgraded my laptop, but now Ubuntu 7.10, which I installed on an external HD, won't boot.  GRUB loads, Ubuntu seems to start loading, then it stops.  The screen just stays blank (I never got around to fixing the widescreen resolution thing, so I've never seen a boot up screen).  I guess the hardware is too different.  Is there any way of rescuing this installation?  It would be convenient if there is, but there's nothing to lose if I have to resort to formatting and reinstalling.

If I do indeed have to reinstall, I'd rather install it on my signifincantly larger internal hard disk.  To do this, I've read eleswhere that one must defrag the windows partition to get all the data to the start of the partition, and use partitioning software to create the new partition without losing any data on the windows partition.

The question is, *are there any free partition managers that are up to the job*?  I don't want to lose any data on my windows hard disk.  Can anyone recommend something for the job?

Thanks!

---

### Post by aashay on 2008-04-09
You dont need to defrag to resize a partition. Any decent partition manager would allow a partition resize without data loss. Try gparted```
sudo apt-get install gparted
```which comes with Ubuntu. Regarding rescuing the old installation, I would say No, but I'm not too sure.

---

