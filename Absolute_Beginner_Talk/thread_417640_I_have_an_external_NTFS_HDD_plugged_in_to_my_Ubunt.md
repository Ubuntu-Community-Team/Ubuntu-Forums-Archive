---
title: "I have an external NTFS HDD plugged in to my Ubuntu box how can I write safely to it?"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by braveerudite on 2007-04-21
I have an external NTFS HDD plugged in to my Ubuntu box how can I write safely to it?

---

### Post by MxGB on 2007-04-21
Install the ntfs-3g and ntfsprogs packages for NTFS read/write support. You may need to manually mount the partition(s) on the drive by using the 'mount.ntfs-fuse' command in a terminal.

EDIT: There is also a graphical tool available in the ntfs-config package for setting up read and write for NTFS partitions.

---

### Post by braveerudite on 2007-04-21
> **MxGB said:**
> Install the ntfs-3g and ntfsprogs packages for NTFS read/write support. You may need to manually mount the partition(s) on the drive by using the 'mount.ntfs-fuse' command in a terminal.

EDIT: There is also a graphical tool available in the ntfs-config package for setting up read and write for NTFS partitions.

Thx man ... it work :)

---

