---
title: "Deleting Read Only files"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by will71110 on 2007-01-07
I'm at a lost.  I FTP some files from my windows XP to my ubuntu extra hard drive and now I cannot delete them because they were put on there as read only files.  Does anyone know how to rid of these? I tried sudo rm -R /media/harddrive2/pictures but that gave me the same errors as if I was using the GUI.  Thanks for any help :)

---

### Post by will71110 on 2007-01-07
Ah...got it working now.  I did a reboot and now I can delete them.  For some reason, when the GPROFTPD locked up, it cause my entire extra drive to be read only.

---

### Post by will71110 on 2007-01-08
Just found out there is something wrong with my extra hard drive.  The drive goes to read only after you start putting a lot of files on it (sounds more like the file system on the drive is actually locking up).  Is there a utility that will scan the sectors of the hard drive and mark it?  I've looked but unsure what I should use.

---

