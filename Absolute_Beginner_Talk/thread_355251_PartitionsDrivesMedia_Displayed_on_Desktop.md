---
title: "Partitions/Drives/Media Displayed on Desktop"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by Thrashers7989 on 2007-02-07
Hey everybody:

Today is my second day on Ubuntu and I'm loving it a whole lot better than *gulp* Windows Vista.

Can anybody tell me if there's an easy way to decide what partitions display on the desktop?

More specifically: my Master Boot Record partition is on my desktop and I don't want it there, but I do want my windows partition and also my File System to show up on the desktop. Is there any easy way I can manage this?

Also is there a way for removable media (USB drives, DVDs) to show up on the desktop upon insertion?

Thanks!

Bryan

---

### Post by jordanmthomas on 2007-02-07
Anything that gets mounted in /media/* will show up on the desktop.
If you don't want...say your Windows partition to show up on the desktop mount it somewhere other than /media/windows (maybe /mnt/windows)

USB drives and CDs should already show up on the desktop.  If not, make sure they are auto-mounting (system -- preferences -- removable media) and make sure nautilus is configured to show the icons.

in gconf-editor, it's in /apps/nautilus/*something*
I don't have gconf-editor installed so I am not sure exactly where

---

### Post by Thrashers7989 on 2007-02-07
Another newbie question...how do you mount it elsewhere? I can't just move the folder.

Say I want to mount hda1 from /mount/hda1 to /mnt/hda1. How can that be done and will it stop appearing on my desktop (like I want it to)?

---

### Post by Duck2006 on 2007-02-07
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

This one is good reading
Just change the mount points to where you want then to show up

---

