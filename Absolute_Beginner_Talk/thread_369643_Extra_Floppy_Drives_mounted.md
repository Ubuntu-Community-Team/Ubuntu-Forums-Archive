---
title: "Extra Floppy Drives mounted"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by Meson on 2007-02-24
My laptop does not even have a floppy drive.  I had an installation of Ubuntu which I deleted and reinstalled today.  The original had no problems with the floppy (installed about 2 days ago).  The one I'm on now shows "Floppy 1" and "Floppy Drive" in the Computer window.  Both installations are from the same disk and both were updated completely.  They have roughly the same packages.

I'm sure this is just an edit of something in /etc/ maybe an init file.  I'm not sure where to look though.  Also, is there a place to address this in the GUI?

---

### Post by chggr on 2007-02-26
check if there are duplicate entries for the floppy drive inside the file /etc/fstab. To open it with gedit, use this command:

sudo gedit /etc/fstab

PS. Be carefull on the changes you make to that file!!

---

