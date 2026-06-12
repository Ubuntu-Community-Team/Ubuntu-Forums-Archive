---
title: "Hard drive hotplugging question"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by Bothered on 2007-11-17
I have an external hard drive that I use for backups. I want the hard drive to be accessible to root only, but I've noticed that the hard disk device file is in the group "plugdev". That means that any user can, for example, format the drive and destroy the backups. Is there any way to change the group of the device file, bearing in mind that the drive is usually hotplugged?

If not, can I simply remove all users from the plugdev group (by editing /etc/groups manually)? What problems would doing this cause?

---

### Post by ddrichardson on 2007-11-17
Other users will not be able to mount any removable media this way. The simplist solution is to mount the drive in fstab with the nouser option meaning only root can mount it, and noauto so it isn't mounted at boot.

---

### Post by Bothered on 2007-11-18
Would that help? It's the device file that is writable by the plugdev group - i.e. /dev/sd[drive] files. I didn't think fstab controlled permissions of the device files?

---

### Post by ddrichardson on 2007-11-18
It doesn't really control permissions, but it would prevent the file system from being mounted by anyone other than root.

---

