---
title: "Force Check DISk (like 30xboot check)"
date: 2005-12-06
forum: Absolute Beginner Talk
---

### Post by nitricacid on 2005-12-06
what do I do to run a disk check like the one after booting 30times it check on it's own?
Further more I have a few bad I\O sectores that I noticed the last time it check the disk, how do i fix them?

---

### Post by cilynx on 2005-12-06
most likely, "fsck.ext3 /dev/hda1"

fsck == filesystem check
you may need to replace ext3 with ext2 or reiserfs depending on what filesystem you're using.

/dev/hda1 is the first partition on the first IDE hard drive.  If that's not the partition you want to check, replace it with the proper one

[edit]
btw: don't try to fsck a mounted partition
[/edit]

[continued edit]
check out "man badblocks" for getting around those
if you don't have it installed at the moment, you can see an online version of the man page here: [http://www.die.net/doc/linux/man/man8/badblocks.8.html](http://www.die.net/doc/linux/man/man8/badblocks.8.html)
[/continued edit]

---

