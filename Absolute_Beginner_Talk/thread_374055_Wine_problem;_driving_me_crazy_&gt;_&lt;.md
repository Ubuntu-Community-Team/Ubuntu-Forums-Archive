---
title: "Wine problem; driving me crazy &gt;_&lt;"
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by ETSNMGA on 2007-03-02
So I installed Wine, but there's a problem. 

I can't even run winecfg (or anything wine related for that matter); whenver I do I get the following error:

err:ntdll:RtlpWaitForCriticalSection section 0x7eaa6160 "x11drv_main.c: X11DRV_CritSection" wait timed out in thread 000c, blocked by 000b, retrying (60 sec)

Then, the winecfg window pops up, but the entire thing's frozen, I can't click anything, and it usually ends with me killing winecfg.

I checked my xserver and all that, it seems to be in good working order.

Can anyone help me please? Thank you very much!

---

### Post by steven8 on 2007-03-02
Have you tried removing wine and reinstalling?

> sudo aptitude remove wine

---

### Post by ETSNMGA on 2007-03-02
Yeah; no change whatsoever.

---

### Post by Patrick K on 2007-03-02
Try it with purge or use Synaptic and "mark for complete removal" then download it again and install. With a regular uninstall the package and config files remain on the computer. Complete removal should give you a fresh start.

---

