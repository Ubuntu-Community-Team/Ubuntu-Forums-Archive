---
title: "adding ubuntu partition to parallel, mounting problem"
date: 2009-12-05
forum: Apple Hardware Users
---

### Post by lilmienboy on 2009-12-05
Some how I'm not able to add the ubuntu partition to parallel through mac osx. It says it not able to mount the ubuntu partition..And when i do try to mount it thru osx disk utility its telling me i need to repair it and reformat it. I'm triple booting with mac osx, win 7, and ubuntu through refit. I set up my installation with ext3 format. thanks for any help.

---

### Post by linuxopjemac on 2009-12-06
> You need to mount it as ext2.
Try the following:
mount_ext2 -o rdonly -x /dev/disk0s3 /Volumes/Linux

Disable automount if enabled via GUI.

got it from here:
[http://www.insanelymac.com/forum/index.php?showtopic=34227](http://www.insanelymac.com/forum/index.php?showtopic=34227)

---

