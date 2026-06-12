---
title: "Quick fstab question"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by Iolo34 on 2007-03-16
I had an issue with Ubuntu 6.10 where my cd-rw and dvd-rw drives were being mounted twice (e.g. cd-rw drive mounted in both /media/cdrom0 and /media/cdrecorder).  I checked the fstab, there's only a single reference to each drive (e.g. /dev/hdc mount to /media/cdrom0). Removing any references to the optical drives in fstab fixes the problem.  My question is then, do optical drives need to be listed in fstab to be mounted properly? If not, where are they added instead?

---

### Post by spd106 on 2007-03-16
I think it's more likely that the /media/cd-recorder etc were just symbolic links to the real mount point. 
You can check with this command **ls -l /media**.

Gnome uses the Gnome-Volume-Manager to automount file systems, have a look at this page for a starter [http://www.togaware.com/linux/survivor/Using_Gnome_Volume_Manager.html](http://www.togaware.com/linux/survivor/Using_Gnome_Volume_Manager.html).

I wouldn't suggest removing any lines of the fstab unless you know what you are doing and even then it's better to make a backup/comment out parts.

---

