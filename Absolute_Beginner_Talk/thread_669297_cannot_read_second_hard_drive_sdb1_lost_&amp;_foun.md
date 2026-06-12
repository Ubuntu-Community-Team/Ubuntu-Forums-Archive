---
title: "cannot read second hard drive sdb1 lost &amp; found contents"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by okkie on 2008-01-16
after upgrading from feisty to gutsy i have second hard drive sdb1 mounted on desktop.the guide i used instructed me on how to set the partitions to save my photos etc.i trust that i accurately followed the guide and that all the files i tried to save are now in the lost &found folder in sdb1.
my problem is i cannot unmount sdb1 or look at the contents. permission is denied.can someone pse. help

---

### Post by mattismyname on 2008-01-18
I think that files showing up in lost+found means the filesystem became corrupted.  I would run fsck to ensure the disk is clean.

If you're getting permission errors when trying to umount the drive, make sure you're trying to do it as root.  From a terminal do "sudo umount /dev/sdb1".

---

### Post by okkie on 2008-02-11
sorry for only coming back now and thanks for your reply.i used your sudo........but there is no reaction

---

### Post by okkie on 2008-02-11
after more attempts harddrive now unmounted.thanks.problem solved.

---

