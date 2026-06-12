---
title: "hard drive recoginition"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by Shilow on 2007-02-12
I installed ubuntu 6.10 and once it was loaded I could not find my slave hard drive. Its partitioned into half 15 Gigs each. I need these files to continue work. Any suggestions?:confused:

---

### Post by jpeddicord on 2007-02-12
Did you check the /media folder? Your hard drive might have been mounted there during installation.

Jacob

---

### Post by nickburns on 2007-02-12
Is you bios seeing the HD?

Is it showing up in Places >> [Your HD]?

---

### Post by Bartender on 2007-02-12
What's on that second drive?  NTFS Windows files?  ext3?

Chances are they're just not mounted.  Check out ftstab posts.

Pop your Ubuntu CD back in and let it spin up to the desktop, then go to Systems>Administration and start up Gnome Partitioner, then take a screenshot if you can or describe what you see.  It should see both HDD's, and you should be able to choose which drive to look at by choosing up in the right hand corner I believe.

Or type in 
```
sudo fdisk -l
```
into terminal and post those results.

Take a look at [aysiu's]("http://www.psychocats.net/ubuntu/mountwindows") website for some tips on how to make Windows partitions automount.

---

