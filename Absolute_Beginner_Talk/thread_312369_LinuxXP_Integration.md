---
title: "Linux/XP Integration"
date: 2006-12-04
forum: Absolute Beginner Talk
---

### Post by Amit Yaron on 2006-12-04
Hi!

I have both Window XP and Ubuntu linux installed on the same machine.
Using disks-admin I've created a link to the files on my XP.
Now the XP is regarded as Read Only file system when browsing from Ubuntu.
My questions are:
1. Can the link to XP be permanent?
2. Can I run the programs in the NTFS partitions using wine? Will installing Wine and copying those programs be enough if I want to run them?

---

### Post by rpkehoe on 2006-12-04
You can, using NTFS-fuse.  Check out this thread [http://ubuntuforums.org/showthread.php?t=142481](http://ubuntuforums.org/showthread.php?t=142481)

---

### Post by Harmshi on 2006-12-04
The link to XP can be permanent if you mount the XP harddisk at startup. So figure which drive it is (hda1 probably). I have tried to run some games from my NTFS drive using Wine, and it works in some cases. As always, not all WinXP programs run well using Wine.

---

### Post by Amit Yaron on 2006-12-04
Thanks,

I made the link permanent, but now the file system is read-only.

---

### Post by bodhi.zazen on 2006-12-04
For rw access to ntfs try [ntfs-3g](http://doc.gwos.org/index.php/NTFS-3g)

---

