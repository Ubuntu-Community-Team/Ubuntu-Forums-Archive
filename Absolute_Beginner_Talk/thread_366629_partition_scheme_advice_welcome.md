---
title: "partition scheme: advice welcome"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by bracc0 on 2007-02-21
Hi everybody.
I have a PC with two HDD IDE.
The first HDD size is 160 Gb and contains WinXP SP2 Home edition.
The second HDD size is 80 Gb and contains WinXP data in a single partition.

I would like to install ubuntu in the second HDD. In order to accomplish this, my thought is to shrink the NTFS partition and to create a 2GB partition for the swap area and a 25 GB partition for "/".
the partition order will be:
[LIST]
[*]NTFS
[*]swap
[*]/
[/LIST]

Does anybody see anything wrong in this? Any better idea?
Will the such an ubuntu installation manage the dual boot?

Thanks in advance

---

### Post by mikewhatever on 2007-02-21
That setup should work. Install GRUB to the MBR of the second HDD, some found it useful to unplug the first HDD duiring installation.
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

---

### Post by bracc0 on 2007-02-26
> **mikewhatever said:**
> That setup should work. Install GRUB to the MBR of the second HDD, some found it useful to unplug the first HDD duiring installation.


Mike,
thanks for your clarification.
I installed ubuntu following your recommendation and it went (almost) fine.
I opened a new thread about my current situation:
[http://www.ubuntuforums.org/showthread.php?t=370047](http://www.ubuntuforums.org/showthread.php?t=370047)

Thanks again.
Claudio

---

