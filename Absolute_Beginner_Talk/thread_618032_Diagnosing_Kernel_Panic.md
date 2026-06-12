---
title: "Diagnosing Kernel Panic"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by cnschulz on 2007-11-20
Hi, I have been running fiesty and then upgraded gutsy with no problems. My machine has been stable and untouched for quite a while.

I have just recieved a kernel panic. "kernel panic fatal exception in interrupt" i believe this is due to disk activity. I noticed it was happening when Munin was running so i disabled it. The machine then ran fine (only tested 30 mins) then id did an fsck and recieved the panic again. It looks bad! FSCK will crash every time it runs... occasionally it will recover to the maintenance login but most times i get a panic.

The crashes always seem to involve disk operations on the swap file. I believe Munin interrogates the swap file for reporting purposes. Can I just delete this file somehow? Does the fact that fsch crashes the machine indicate a disk fault or could it be something else?

I understand this problem is a little tricky to resolve however I have not seen a consistent method for tracing the source of the problem.

Can you suggest what logs/processes/methods I could use to find and hopefully resolve this issue?

cheers

c.

---

### Post by angryfirelord on 2007-11-20
Sounds like something didn't update quite right. First thing is to re-install the linux-image package and see if that corrects any kernel panics. Next, browse over to **/var/log** and see if anything pops out at you.

If googling doesn't work, then do a re-install of Ubuntu. If fsck doesn't complain, then it was probably an update issue with the kernel and/or fsck. If the problem resumes, then it could be a hard disk problem.

---

### Post by quickshade on 2007-11-20
Personally I would get a live CD and delete you swap file and see if it boots up. That way you can have temp access to your system. I had a problem similar to this in which it kept trying to scan my swap file but couldn't. Sometimes I would get a kernel panic or system boot failure. Others it would enter a maintenance screen and I would have to ctrl-d to finish the boot. I ended up having to hide my swap file from the scan tool and that fixed the problem. But your might not be the same.

---

### Post by cnschulz on 2007-11-22
Hi, 

Sorry, the upgrade was quite some time ago... i wasnt clear on that.

BUT it turned out to be dud memory. Removed offending chip and all is well (albeit slower!)

Thanks.

c.

---

