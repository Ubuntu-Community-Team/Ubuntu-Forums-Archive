---
title: "How do I remove links to mounted drives on my desktop without unmounting the drive?"
date: 2006-07-14
forum: Absolute Beginner Talk
---

### Post by southerngrey on 2006-07-14
I have recently installed dapper drake in a dual boot system with xp-pro and xp-64.  I have mounted the windows drives so that I can access the information but it also places a link on the desktop which I cannot figure out how to remove.  Is there a simple gui fix or terminal command to remove these? Thanks

---

### Post by aysiu on 2006-07-14
You probably mounted the partitions to /media or /mnt

If you mount them to those directories, they get automatically put on your desktop.

One way around this is to change the mount point. It may be simpler for you to do this, though: Alt-F2 ```
gconf-editor
``` Apps > Nautilus > Desktop > Volumes Visible

---

### Post by southerngrey on 2006-07-14
worked like a charm.  Thank you very much.

---

### Post by Kelderkeuken on 2006-07-17
Thank you, was looking for this as well. :-D

---

### Post by timefortea on 2006-08-09
Me too. Thanks!

---

### Post by spiral777 on 2006-08-09
If you don't want any icons for partitions, go to Configuration Editor under Applications (you may have to enable config ed. through alacarte menu editor)

When it opens, go to Apps<Nautilus<Desktop and uncheck "volumes visible" 

That will keep the volumes' icons from appearing

---

