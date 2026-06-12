---
title: "Uninstalling Ubuntu from PowerBook"
date: 2006-07-09
forum: Apple PPC Users
---

### Post by dreamcove on 2006-07-09
I installed Ubuntu 6.06 on my PowerBook and would like to know how to uninstall it.  Its a nice operating system, but, in practice, I would only use it on my desktop system.

I understand how to remove the Ubuntu partitions and resize my Mac OSX partition back to its original size.  What I'm concerned about is yaboot.  How do I uninstall that without completely reinstalling my system from scratch?

Thanks.

---

### Post by pindar on 2006-07-09
Boot into OS X and, under System Preferences/Startup Disk, choose your OS X partition as your startup system. This will bypass yaboot. You can then just destroy the partition on which yaboot has installed its bootloader, and it'll be gone for good.

---

