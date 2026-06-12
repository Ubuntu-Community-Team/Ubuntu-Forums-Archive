---
title: "USB woes"
date: 2012-12-12
forum: Any Other OS
---

### Post by SumitM on 2012-12-12
I'm running Linux Mint Live disk with persistence. I installed NTFS configuration tool to understand why my USB enclosed HDD get corrupted every time I unmount it. Almost all Linux flavors detect my USB enclosed HDD (This HDD is a laptop internal HDD with SATA port) as internal HDD. Is there any solution to force linux to detect this USB enclosed HDD as External/portable HDD? I tried Ubuntu 12.04, Ubuntu 12.10 and Linux Mint 14 and they all corrupt my HDD after unmount operation. I even try to restart linux while HDD is still mounted....STILL CORRUPTED. It's working fine with windows xp, 7 and windows 8. Please help me.... it's HITACHI 250GB laptop internal (3.5") HDD.

---

### Post by squakie on 2012-12-12
> **SumitM said:**
> I'm running Linux Mint Live disk with persistence. I installed NTFS configuration tool to understand why my USB enclosed HDD get corrupted every time I unmount it. Almost all Linux flavors detect my USB enclosed HDD (This HDD is a laptop internal HDD with SATA port) as internal HDD. Is there any solution to force linux to detect this USB enclosed HDD as External/portable HDD? I tried Ubuntu 12.04, Ubuntu 12.10 and Linux Mint 14 and they all corrupt my HDD after unmount operation. I even try to restart linux while HDD is still mounted....STILL CORRUPTED. It's working fine with windows xp, 7 and windows 8. Please help me.... it's HITACHI 250GB laptop internal (3.5") HDD.

You are doing what is called hijacking a thread - this thread is not about your problem.  When you can't contribute to a solution for a thread, it's time to open your own thread about your problem.

---

### Post by lisati on 2012-12-12
*Moved to **Other OS/Distro Talk**.*

---

### Post by sudodus on 2012-12-12
Hi and welcome to the Ubuntu Forums!

> **SumitM said:**
> Almost all Linux flavors detect my USB enclosed HDD (This HDD is a laptop internal HDD with SATA port) as internal HDD. Is there any solution to force linux to detect this USB enclosed HDD as External/portable HDD?

I don't understand. If it is a laptop internal HDD with SATA port, it should be reported as an internal HDD. Why do you want linux to report it as External/portable HDD?

Please explain again!

And what do you mean by unmounting? Do you mean disconnecting it? There is a linux command to run
```
umount
``` and there is an eject symbol in the file browser, that you should click before disconnecting the partition or drive. This logical unmounting corresponds to 'remove safely' in Windows.

Anyway, give us more details, and we will try to help :-)

---

