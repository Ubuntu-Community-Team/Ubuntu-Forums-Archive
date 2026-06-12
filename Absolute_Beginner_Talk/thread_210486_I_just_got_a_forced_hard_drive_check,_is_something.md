---
title: "I just got a forced hard drive check, is something wrong?"
date: 2006-07-06
forum: Absolute Beginner Talk
---

### Post by Cherry Popper on 2006-07-06
The forced check happened during boot up, when those orange text are scrolling. I'd take a screenshot but I wasn't at my desktop yet so couldn't but the forced check says something along the lines of "/dev/hda1(??) has been mounted 30 times without check. Forced checking"

Something wrong with my hard drive? After the check, Ubuntu booted normally though, no error messages or anything. :confused:

---

### Post by woedend on 2006-07-06
nothing wrong.  by default its to be checked every 30 mounts.  It's a good thing.  You CAN disable this though, if you want, using tune2fs.  If you really want to i'll list the command, but i'd leave it alone.

---

### Post by professor_chaos on 2006-07-06
No by default, your system does a fsck file check every 30mounts. Call it preventitve maintainece.

---

### Post by atoponce on 2006-07-06
Nope.  Nothing wrong.  This is normal behavior.

---

### Post by Cherry Popper on 2006-07-07
Ah okay, thanks for the replies everyone, I had been playing around with Compiz  *just* the day before and was afraid that I had damaged something.

---

