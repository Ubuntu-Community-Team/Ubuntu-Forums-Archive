---
title: "Boot sector error during boot"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by freesitebuilder on 2007-02-25
I've just partitioned to allow dual booting, and installed Ubuntu 6.06 LTS from LiveCD. Although it runs OK, during boot I get an error:
DOSFSCK 2.11 Difference between boot sector and backup

with (presumably) a list of the sectors. After about 20 seconds it continues to boot and runs OK. Windows is also running OK.

Is this an error that I made during partitioning?

TIA

---

### Post by n8bounds on 2007-02-25
It's actually mounted your windows FAT32 partition and basically done a chkdsk on it and is reporting errors.  You can tell it to NOT mount your windows partition in your /etc/fstab file, fix your windows partition, ignore the error or maybe delete windows.  Your choice.

---

