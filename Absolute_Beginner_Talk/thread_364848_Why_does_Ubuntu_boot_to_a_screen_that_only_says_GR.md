---
title: "Why does Ubuntu boot to a screen that only says GRUB?  (Toshiba Satellite M35-S456)"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by xltblx on 2007-02-18
I installed Ubuntu 6.06 onto a Toshiba Satellite M35-S456.  I had the installer erase the entire hard drive and partition it by itself.  When the install finishes (which it does just fine) it tells me to remove the CD, which I do, and then it restarts and only boots to a screen that says GRUB in the upper left hand corner and just sits there.  Help!  What do I do to make it boot?

---

### Post by moshuptrail on 2007-02-18
If it installed correctly, grub would list a few choices, at least 2.  One to boot dapper, and another to boot in recovery mode.  So things did not go well.  I suggest using the Gparted Live CD to review the partitioning and be sure all partitions are properly formatted.  Then try re-installing.  

Afterthought: The Ub Live CD works okay, right?

---

### Post by xltblx on 2007-02-18
UB Live works OK.  It is currently in the middle of installing 6.10, so I'll see if that works, if it doesnt, then I'll try what you just said.  Thanks for the help, I'll keep you posted!

---

### Post by xltblx on 2007-02-18
6.10 still has the same error.  I cannot seem to find what is wrong.  What should the partition map look like exactly?  I just let the system do it automatically--what is wrong with that?

---

### Post by koshari on 2007-02-18
iam willing to take a punt theres a recovery partition somewhere creating chaos.

---

### Post by moshuptrail on 2007-02-18
I found that the Live CD would skip formatting drives if it thought they were already formatted.  (or maybe it just does a "quick" format)  I had several installs that didn't quite work, notably when a partition was being changed from one type to another (NTFS to ext3 for example)  I had to use the Gparted Live CD to manually partition and format the HD.  Only then did the install work.

---

