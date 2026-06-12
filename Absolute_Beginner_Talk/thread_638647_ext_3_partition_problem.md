---
title: "ext 3 partition problem"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by pandaxcore on 2007-12-12
"The ext3 file system creation in partition #1 of SCSI1 (0,0,0) (sda) failed."

this is during the partitioning phase after i put in my name and password.
can anyone tell me whats goin on?
__________________

---

### Post by kefurd06 on 2007-12-12
this may not be the problem, but when i'm reconfiguring my partitions, occasionally partitions will decide to (rather aggressively) remount, even during the partitioning process, so i have to constantly unmount them again before gparted throws an error (right-click a drive that appears on the desktop > unmount)

---

### Post by pandaxcore on 2007-12-12
> **kefurd06 said:**
> this may not be the problem, but when i'm reconfiguring my partitions, occasionally partitions will decide to (rather aggressively) remount, even during the partitioning process, so i have to constantly unmount them again before gparted throws an error (right-click a drive that appears on the desktop > unmount)odd, im running off the live cd and this is in the attempt to install, so im not sure whats happenin



also this is what the summary right before i continue after i put in my name and password says



The partition tables of the following devices are changed:
 SCSI1 (0,0,0) (sda)

The following partitions are going to be formatted:
 partition #1 of SCSI1 (0,0,0) (sda) as ext3
 partition #5 of SCSI1 (0,0,0) (sda) as swap

---

### Post by floke on 2007-12-12
See my reply to your double post:

[http://ubuntuforums.org/showthread.php?p=3938789#post3938789](http://ubuntuforums.org/showthread.php?p=3938789#post3938789)

---

