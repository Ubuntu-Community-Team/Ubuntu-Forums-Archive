---
title: "Mounting NTFS partitions."
date: 2005-11-26
forum: Absolute Beginner Talk
---

### Post by paulozzzz on 2005-11-26
People,

I could not find any "recipes" in the Cookbook as to mount NTFS partitions.

How do I mount two NTFS partitions (one is the main partition and the other is the first logical partition of the extended partition of hda1) for read/write access?

---

### Post by aysiu on 2005-11-26
NTFS doesn't get read/write access in Linux.
It's read-only.

Follow these directions: [http://www.ubuntuguide.org/#automountntfs](http://www.ubuntuguide.org/#automountntfs)

The directions assume your NTFS partition is /dev/hda1
If you want to know what it really is type ```
sudo fdisk -l
``` in a terminal:

Applications > Accessories > Terminal (Breezy)
Applications > System Tools > Terminal (Hoary)

---

### Post by paulozzzz on 2005-11-26
Thanks.

Just another question:

The fdisk output was:

/dev/hda1   *           1        1529    12281661    7  HPFS ou NTFS
/dev/hda2            1530        1819     2329425    f  W95 Ext'd (LBA)
/dev/hda3            1820        2432     4923922+  83  Linux
/dev/hda5            1530        1788     2080386    7  HPFS ou NTFS
/dev/hda6            1789        1819      248976   82  Linux swap / Solaris

In Windows I have C: and D: drive letters.

I recognize hda1 as C:, but hda2 and hda5 are confusing me.  To begin with my HD was supposed to have just four partitions.  Which of them is D:, the drive that holds my data?

---

### Post by paulozzzz on 2005-11-26
Thanks, aysiu.  As I am experimenting with Linux, I just tried both to see what happened.  hda5 is the D: drive of Windows.

---

