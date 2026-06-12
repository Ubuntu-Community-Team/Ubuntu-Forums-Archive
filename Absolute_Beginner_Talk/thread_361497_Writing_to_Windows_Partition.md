---
title: "Writing to Windows Partition"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by scwinn on 2007-02-14
UBUNTU mounts mt Windows partition. Thanks. But I cannot write to it. I change the properties to read/write in Gnome, but alas same error.

---

### Post by housam on 2007-02-14
Remount windows partitions using this guide.
[http://www.psychocats.net/ubuntu/mountwindows]("http://www.psychocats.net/ubuntu/mountwindows")

---

### Post by newlinux on 2007-02-14
Linux does not natively write to NTFS. There are some drivers available, but they have a certain amount of risk involved (such as ntfs-3g [http://www.ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-3g+howto)](http://www.ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-3g+howto)). You can install fs-driver (fs-driver.org) in windows to be able to read and write to ext3 (linux) which is safer, or you can make a "transfer" partition in FAT32, which both Windows and Linux can natively read and write to.

---

