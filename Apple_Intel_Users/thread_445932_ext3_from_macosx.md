---
title: "ext3 from macosx"
date: 2007-05-16
forum: Apple Intel Users
---

### Post by nitrofurano on 2007-05-16
accessing as read-write the hfs partition from ubuntu-feisty is not hard task at all - but how can i access the ext3 partition from macosx? do someone know?

---

### Post by ronocdh on 2007-05-16
> **nitrofurano said:**
> accessing as read-write the hfs partition from ubuntu-feisty is not hard task at all - but how can i access the ext3 partition from macosx? do someone know?
[Enjoy!]("http://sourceforge.net/projects/ext2fsx/")

---

### Post by Chrisj303 on 2007-05-16
^ if the GUI dosen't want to mount your ubuntu partition (common bug with v1.4d) then you need to mount it with the terminal. I create a folder on my desktop, and name it UBUNTU. Then in a terminal:

sudo mount_ext2 /dev/disk0s3 /Users/username/Desktop/UBUNTU


*you need to change 'disk0s3' for wherever your ubuntu partition is. 

At this point is easy to think that it has not worked, as the GUI does not update.

From the finder menu  GO > GO TO FOLDER > (Point to UBUNTU folder)

*you may need to do this twice

Your ubuntu partition will show as a drive on your desktop.

I prefer to manually unmount via the terminal as well, to do this :

sudo umount /dev/disk0s3 - again changing disk0s3 to your ubuntu partition.


*note, then when mounted in this way, you WILL be able to access the options ext2fsxmanager offers from it's system pref's pane.


Hope that helps!

chrisj303

---

