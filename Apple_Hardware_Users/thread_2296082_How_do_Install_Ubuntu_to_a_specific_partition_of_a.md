---
title: "How do Install Ubuntu to a specific partition of a External hard drive?"
date: 2015-09-23
forum: Apple Hardware Users
---

### Post by Turon on 2015-09-23
I have a External hard drive with two partitions one is NTFS format and the other is Mac OS Extended (Journaled). I've been trying to install to the Mac OS Extended (Journaled) one as well as the NTFS one and they both come up with this error message which says that it can not find something called a "root file system". I don't even understand what the the installation demands...

---

### Post by Dennis N on 2015-09-23
In the Ubuntu installer, use the "something else" option on the "preparing to install" screen. Then, on next screen, select the partition for installation, click on change, and specify it to have ext4 journaled file system, mount as /. Put a check in the format box. You also need a swap partition if not already present. At bottom, pay attention to boot loader location - usually to the same disk (sdb perhaps) - depends on your disk designations.

---

### Post by Turon on 2015-09-23
Thanks! Installation has now began. Though for the last hour it's been stuck with "detecting file system" and it been saying stuff like "can't find device agent" and "imput: authorization for BB:09:8A:BD:AC:0C operation not permitted (-1)", it's been repeating these sort of coments over and over, what does this all mean?

---

