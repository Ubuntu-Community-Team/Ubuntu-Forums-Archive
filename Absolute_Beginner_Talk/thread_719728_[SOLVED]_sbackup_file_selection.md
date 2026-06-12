---
title: "[SOLVED] sbackup file selection"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by oxo2oxo on 2008-03-09
I may be being daft, but in sbackup how do I select files that are on an external drive to back up. I can backup to the external drive but cannot see how you select the drive if your source files are on it

---

### Post by Rocket2DMn on 2008-03-09
The drive has to be mounted for you to access it, and in linux we mount other drive somewhere on the filesystem, typically in the /media directory.  Normally drives automount there unless you specified something different in /etc/fstab, so say when you plug the drive in it appears on your desktop as "usbdisk".  The mount point for that drive would be at /media/usbdisk
So, from sbackup, you would go to the Include tab and hit Add File, then navigate to the /media/usbdisk directory.

---

### Post by oxo2oxo on 2008-03-09
Many thanks, I forgot the /media/ extension for disk !

---

