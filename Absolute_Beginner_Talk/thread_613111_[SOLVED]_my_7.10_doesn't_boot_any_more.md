---
title: "[SOLVED] my 7.10 doesn't boot any more"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by netimen on 2007-11-14
All was OK for almost a month. But now 7.10 starts booting, the orange progress line goes up to 1/3 and then it shows black screen in text mode with only a cursor and the system reacts only on double Ctrl+Alt+Del. The hard drive lamp is on.

I tried to boot in safe mode. It goes up to the message about my sda3 have been mounted too many times - check forced. Then all hangs.

---

### Post by Inxsible on 2007-11-14
The forced check is normal. These checks often run after about 30-35 mounts of the partition. Let it run to fruition. If you notice you will see a small percentage meter on the right. Let it run and you should be able to log in.

---

### Post by netimen on 2007-11-14
No, the problem is that there is NO percentage. I have already seen such checks before and there were this percentage, but now there isn't!

---

### Post by Inxsible on 2007-11-14
Boot up using a live CD and then run fsck on each of your partitions. Then try booting normally.

---

### Post by netimen on 2007-11-14
should i mount them before check?

---

### Post by Inxsible on 2007-11-14
NO. you should never mount the partitions while doing fsck.

---

### Post by PointyWombat on 2007-11-14
No. Only run fsck on unmounted file systems.

---

### Post by alienexplorers on 2007-11-14
Just run fsck on them.  Do not mount the drives!!!

---

### Post by schorsch on 2007-11-14
No, never ever check a mounted filesystem as it could cause severe damage to the filesystem! Only check unmounted filesystems.

---

### Post by netimen on 2007-11-14
It starts and then suddenly quits - no long checking as it is usually. only this output is written
```
fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
/dev/sda3: clean, 32618/4521984 files, 2428454/9038570 blocks

```

---

### Post by netimen on 2007-11-14
The problem disappeared - I have waited a bit longer and the system booted successefully! Shame on me, however it was quite odd to see a black screen in text mode appearing in the middle off boot process.

Thanks to all who replied.

---

### Post by Inxsible on 2007-11-14
> **netimen said:**
> The problem disappeared - I have waited a bit longer and the system booted successefully! Shame on me, however it was quite odd to see a black screen in text mode appearing in the middle off boot process.

Thanks to all who replied.Patience is a virtue :D

Mark your thread as solved. Thread Tools>>Mark Thread as solved

---

