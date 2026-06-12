---
title: "backup and restore clonezilla"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by bugler on 2007-04-24
Got a question on clonezilla and backup and restoring.

I downloaded the latest clonezilla 1.0.25 i think... as of apr 18.

My scenario:
I am dual-booting winxp and ubuntu (previously 6.10 and currently 7.04).  See attached screencap for partition info.  
I want to backup and restore my ubuntu partitions in order for me to experiment and be able to restore when.. not if.... I screw it up.
I successfully burned clonezilla livecd and booted and backed /sda6 and /sda7 to /sda1 ntfs partition.  (see screencap on contents).  
My questions:

I want to burn the info to a dvd, what do I burn? The whole folder 2007-4-23-11-img?
When I need to restore these partitions, I boot livecd choose restore and then what??  How do I choose dvd?
clonezilla did not allow me to choose swap part.  So, when I do restore, do I have to gparted and add swap?
Little confused at this point.
What happens if drive blows up and need to replace drive?  Can I restore what I have to the new hard drive?

Would love to get some feedback on this.

P.S.  I tried systemrescuecd and it took forever to backup.

Thanks Bugler

---

### Post by SgtDude on 2007-06-12
I've been working with clonezilla (full install, not live cd) for the last few weeks.  It seems that there's no "backup to/restore from CD/DVD" option.  It seems more geared towards systems administration shops where we generally keep images on external hard drives and use them more for cloning machines than backup purposes.  [Ghost for Linux]("http://sourceforge.net/projects/g4l") has an option to break the image in to 2GB (or whatever) sized chunks, but I havn't tested actually restoring from DVDs with these chunks on them.

I know this reply is 2 months late, but maybe someone else will find it informative.

---

### Post by perham on 2008-06-09
partimage has all the functionalities you want. just download [system rescue cd]("http://www.sysresccd.org/Main_Page")
there you can mount dvd, and restore from the dvd drive using partimage.

---

### Post by MrKlean on 2008-06-09
Another thot is remastersys.  it will make a live cd/dvd of your system.  If anything happens, you can put  the cd in and restore it :)

---

