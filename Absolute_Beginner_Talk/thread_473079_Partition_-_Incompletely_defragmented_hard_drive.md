---
title: "Partition - Incompletely defragmented hard drive"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by ChrisE on 2007-06-13
This isn't exactly an ubuntu question per se, but it's related, and I figure it's something somebody here has faced before.

I've recently cleaned a lot of files off my hard drive, with the hopes of partitioning it and running ubuntu on the new partition.  However, after running the windows defragmenter, while most of the files are nicely positioned on the "left" side of the hard drive, there's a small section on the far "right" that won't really move.

Obviously, partitioning the hard drive would be simpler if I could get those files to move.  However, windows doesn't seem to want to do it.  So, is there any sort of free partition manager that I can run to shift these files?

Thanks,
chris

---

### Post by Mazza558 on 2007-06-13
Sounds like system files. They are usually not affected by defragging whilst Windows is running. You'll need a defragmenter that runs at boot.

---

### Post by Shazaam on 2007-06-13
What Mazza said. Boot Windows into "Safe Mode" and defragment.

---

### Post by wreti on 2007-06-13
There are a few free partition managers out there. If you're using XP try Cute Partition Manager @ [http://www.cutepm.com/](http://www.cutepm.com/)   If that one doesn't work you can do a google search for more. If you're using Vista you can manage partitions by right clicking your C drive and selecting Manage.

---

### Post by bodhi.zazen on 2007-06-13
I think you can partition without worrying about every last fragment ...

Is it even possible to completely defragment a NTFS partition ?

---

### Post by jhenager on 2007-06-13
> **bodhi.zazen said:**
> I think you can partition without worrying about every last fragment ...

Is it even possible to completely defragment a NTFS partition ?
A complete backup and restore will do that.
This is one thing about NTFS that I don't like. The MFT is difficult to defrag.
BTW, I found a pretty good Windows defrag tool the other day. jkdefrag seems to do a good job.

---

