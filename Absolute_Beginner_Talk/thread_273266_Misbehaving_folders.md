---
title: "Misbehaving folders"
date: 2006-10-07
forum: Absolute Beginner Talk
---

### Post by SunnyM on 2006-10-07
I'm having trouble with three folders on hdb (secondary hard drive). It's fat32 , if that makes a difference. 2 of the folders (one of which was previously my "My Pictures" folder on windows are locked, and when I try to edit/delete files, move files to them, etc, they act like they're system files.

The third folder (named 1) is one I want to delete, but when I try to delete it I get an error message that says
```
Error "I/O error" while deleting "/media/windows/icons/1".
```

Any help fixing any of these problems would be much appreciated!

Thanks in advance!:KS

---

### Post by taurus on 2006-10-07
It's about permissions!!!  Do you mount those two partitions by hand or do you mount them in /etc/fstab?  If you mount them by hand, then how do you do that?  Otherwise, cut and paste your /etc/fstab here then...

```
more /etc/fstab
```

---

### Post by SunnyM on 2006-10-07
I followed this tutorial. [http://https://help.ubuntu.com/community/MountingWindowsPartitions]("http://https//help.ubuntu.com/community/MountingWindowsPartitions")

And there are several folders on there that don't have any problem, just a couple that want to act up. (Thought I should mention that)

---

