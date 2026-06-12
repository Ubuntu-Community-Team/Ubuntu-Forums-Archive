---
title: "Hello hello"
date: 2006-01-05
forum: Absolute Beginner Talk
---

### Post by benserwa on 2006-01-05
Hi! I'm using Ubuntu on my old, secondary computer, so I can set up an FTP server on it and use it's hard drive space for storing things as well as to learn PennMUSH and linux in general. I plan on distributing Ubuntu to my friends since I ordered extra CDs, and I know a bunch of geeks whom I think will appreciate it and use it.

Anyway, my computer has two hard drives installed and darn it, I can't figure out how to mount the second one... I tried to Google that action first but garnished no results.

Here's my 'sudo fdisk -l'... hdb is the one that is not mounted yet.

Disk /dev/hda: 15.3 GB, 15382241280 bytes
255 heads, 63 sectors/track, 1870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1789    14370111   83  Linux
/dev/hda2            1790        1870      650632+   5  Extended
/dev/hda5            1790        1870      650601   82  Linux swap / Solaris

Disk /dev/hdb: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4777    38371221   83  Linux
/dev/hdb2            4778        4870      747022+   5  Extended
/dev/hdb5            4778        4870      746991   82  Linux swap / Solaris

---

### Post by Madpilot on 2006-01-05
Have a look here:
[https://wiki.ubuntu.com/InstallingANewHardDrive](https://wiki.ubuntu.com/InstallingANewHardDrive)

---

