---
title: "Disk check every time I run Windows XP"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by alienexplorers on 2007-05-01
Every time I run Windows Xp and then reboot to go into Ubuntu my system runs a disk check.  If I am just running Ubuntu and do a reboot back into Ubuntu it skips the disk check.  Is this normal or is there something amiss somewhere?

---

### Post by darkrose on 2007-05-01
This is just Ubuntu noticing changes to your XP partition (because you used windows) and checking to see if this is because of errors.

You can stop this by editing /etc/fstab and changing the numbers at the end of the line for the windows partition to 0 0

---

