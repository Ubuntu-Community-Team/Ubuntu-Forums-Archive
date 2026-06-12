---
title: "format partition hfs+"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by mättu on 2007-06-11
can anyone tell me how to format a partition using mac osx's hfs+ filesystem?
I need to do such for a friend of mine.
gparted only does hfs. (seems)
There will be some command-line-magic to deal with this sort of problems, i guess. ;-)

:m)

---

### Post by wkdown on 2007-06-11
*Remember, Google is your friend*

**SEARCH**: ubuntu "hfs+"

**HIT #1**: [http://ubuntuforums.org/showthread.php?t=4411](http://ubuntuforums.org/showthread.php?t=4411)

**SEARCH**: ubuntu "hfs+" partition

**HIT #1**: [http://ubuntuforums.org/showthread.php?t=89960](http://ubuntuforums.org/showthread.php?t=89960)

---

### Post by stami on 2007-06-11
Hi,
I don't think you can format the partition with hfs+, but you can create a partition that the Mac OS X installer recognize during the install. Then you can format with the Utility Disk in OS X installer. Using fdisk you should create a partition, then change the partition type to af.
However you can also create an ext2 partition and then format it with the Utility Disk in OS X installer.

Worked for me, I hope it works for you too! :D

---

