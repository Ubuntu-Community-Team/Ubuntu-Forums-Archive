---
title: "making space for Ubuntu"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by Comcon on 2007-07-01
Hello,
I have two hard disks.I want to copy the windows from c: to d:.Then i will be able to install Ubuntu on the first disk.Any program that it gonna make the tric?
Thanks

---

### Post by bodhi.zazen on 2007-07-01
The gparted live CD will do all that :

GParted:
	Documentation: [Documentation](http://gparted.sourceforge.net/documentation.php)
	Download: [Download Gparted](http://internap.dl.sourceforge.net/sourceforge/gparted/gparted-livecd-0.3.4-6.iso)

Also note partitions are named different in LInux then windows. You might want to read this to avoid altering the wrong partition.

[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

---

### Post by Comcon on 2007-07-01
I have the Ubuntu cd-live.I can use it from there(gparted) is it?

---

### Post by oilchangeguy on 2007-07-01
> **Comcon said:**
> Hello,
I have two hard disks.I want to copy the windows from c: to d:.Then i will be able to install Ubuntu on the first disk.Any program that it gonna make the tric?
Thanks

why would you want to copy from one drive to another? simply open the computer and set the jumpers so that the drive with windows is slave, and the other drive is master. do this before you install ubuntu.

---

### Post by Comcon on 2007-07-01
I want that because the c: is bigger than d:.
I want the bigger for Linux:)

---

### Post by oilchangeguy on 2007-07-01
> **Comcon said:**
> I want that because the c: is bigger than d:.
I want the bigger for Linux:)

linux doesn't really need as much space as windows. unless you are planning to fill it with pictures, music, etc.

---

### Post by Comcon on 2007-07-01
Yes that i am gonna do.
By the way what the deference about ext2 from ext3?
what i should format my disk for Ubuntu?
Thanks

---

### Post by Tyke91 on 2007-07-01
ext 2 and 3 are almost the same, except that ext3 uses a journal to quickly make backups of your disk. 

the main effect is: If your computer crashes (rarely) ext2 will require a diskcheck (like windows) while ext3 will just use the journal to load what worked, resulting in a faster recovery

---

