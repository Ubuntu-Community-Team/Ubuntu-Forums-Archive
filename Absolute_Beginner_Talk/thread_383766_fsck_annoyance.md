---
title: "fsck annoyance"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by V-600 on 2007-03-13
Due to my cmos battery being on the way out, my clock resets everytime I turn the computer off. This is playing havoc with the fsck utility which insists on checking my entire hard disk every time i turn the computer on. A message to the effect "last read, last write was in the future". 45'000 odd days since last check.

For the time being until I replace said battery could someone tell me how to disable fsck and how to re-enable it later.

P.S. That said, do i need to re-enable it. As i understand it fsck checks file system integrity with non journalling file systems such as ext2. Is it necessary if I use ext3 to keep it enabled. It used to only check every 36 mounts and never found problems.

Many thanks for any advice

---

### Post by brettg on 2007-03-14
from the fsck man pages;

The sixth field, (fs_passno), is used by the fsck(8) program to determine the order in which filesystem checks are done at reboot time. The root filesystem should be specified with a fs_passno of 1, and other filesystems should have a fs_passno of 2. Filesystems within a drive will be checked sequentially, but filesystems on different drives will be checked at the same time to utilize parallelism available in the hardware. If the sixth field is not present or zero, a value of zero is returned and fsck will assume that the filesystem does not need to be checked.

ergo, remove field 6 (the last digit) and the drive will not be checked at boot time.

---

### Post by Mr. C. on 2007-03-14
man tune2fs

MrC

---

### Post by V-600 on 2007-03-14
thanks. i'd glanced at the man page but missed it.

---

