---
title: "MacBook Air rEFIt Ubuntu partition won't go away"
date: 2014-06-15
forum: Apple Hardware Users
---

### Post by Liam_OLuachra on 2014-06-15
I installed Ubuntu using rEFIt on my MacBook Air. I removed the Ubuntu partition and re-sized OS X 10.9.2 partition but when I boot up my Mac, Ubuntu option is still there.
I didn't use SWAMP because the tutorial on YouTube told me not to. Please help!

Thank you.

---

### Post by oldfred on 2014-06-16
Moved to the Apple sub-forum.

With PC and UEFI you have to remove entry from efi partition first and then from UEFI. UEFI has its own SRRAM to save boot info.
Do not know if a Mac would be the same also?

---

### Post by PartisanEntity on 2014-06-20
What you can try to do is uninstall rEFit, shutdown and restart your computer, then install it again. It will generate a new boot list that should reflect the changes you made on your partitions.

---

