---
title: "[SOLVED] How To Remove An Item From the Update Manager List?"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by FreewareFan on 2008-02-22
Hello all.  I have done a search, and don't find an answer to this.  I have just today installed Compiz Config Manager, so I can learn it's features.  I run Ubuntu 7.10, and when I first installed CCSM, it wouldn't run.  I found out that the problem was because I was using the newest version.  So, I downgraded to version 0.5.2 as was reccomended, and then the manager program worked just fine in Gutsy.

Problem is, now the Ubuntu Update Manager wants me to update the CCSM program, and I'm not about to do it.   How can I remove CCSM from the list of things that Update Manager wants to update?   It's already asked me every time I reboot to upgrade it, and of course, I do not want to do that.

Any ideas folks?  Thanks!!

FreewareFan

---

### Post by yabbadabbadont on 2008-02-22
System->Administration->Synaptic Package Manager.  Find the package you don't want to upgrade.  Select it.  Then, on the package menu (I think), take the "lock version" or maybe it is "force version" option.

---

### Post by spiderbatdad on 2008-02-22
You could set it to only look for important security updates. System>>Administration>>Update Manager

---

### Post by FreewareFan on 2008-02-22
Thanks much, yabba!!  Worked like a charm.  I appreciate the fast response, and the lesson!



I also did what you advised, spider.  I thought to cover all bases!  

FwF

---

