---
title: "Kernel Update"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by Mongo5000 on 2007-09-01
Been a happy ubuntu user since ditching my ati vid card and getting a decent nvidia one but here is my question.  I remember reading somewhere about when updating the kernel it breaking or messing up your install and vid drivers.

I noticed today the update manager wants to install a new kernel and a couple other things but im afraid to do it since I im too newbish to fix it if it goes wrong.

Should I be worried or just go ahead and install the updates?

---

### Post by por100pre1 on 2007-09-01
This new update is causing problems! Read [this]("http://ubuntuforums.org/showthread.php?t=540178"). Backup your files before proceeding!

---

### Post by Kobalt on 2007-09-01
You can install the new kernel and not remove the old one immediately. If something goes wrong you can still boot on the old one from Grub and wait for a fix to come up.
As fas as I know, this kernel has no issue with nvidia drivers. What drivers did you install? how?

---

### Post by kostkon on 2007-09-01
If you compile the nvidia drivers yourself or use some other tool to install them for you (e.g. Envy, Automatix) then a kernel update will break them. After the update you will have to install them again.

If you use the drivers provided by the official Ubuntu repositories, you will not have any problems with your graphics drivers, after a kernel update.

---

