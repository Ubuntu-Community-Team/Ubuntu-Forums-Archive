---
title: "qtparted 'no device found maybe you're not a root user?'"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by treasurebum on 2007-07-08
Hi guys i'm a ubuntu (using dual boot with xp)  newbie just trying to move around some partitions using qtparted, but when i open it the following error message comes up "no device found maybe you're not a root user?" if i then press ok the programme opens, but there are no drives showing. i have searched for an answer to this problem, but can't find it! Any suggestions?:confused:

Using QTparted v0.4.5-cvs

---

### Post by tchoklat on 2007-07-08
to move or change your partitions you need to boot from a GPartEd Cd. Is this what you are doing. If not burn the GPartEd iso to CD and boot from it. That should work I suspect!

---

### Post by treasurebum on 2007-07-08
oh ok i'll try that:), but why on earth does linux have the option to install qtparted as a partition manager if it cant do anything?:confused::confused:

---

### Post by cookies on 2007-07-08
If it is Kubuntu, press Alt F2 and type kdesu qtparted

If it is Ubuntu, press Alt F2 and type gksudo qtparted

This allows it to run as "Root" and see drives.

---

### Post by treasurebum on 2007-07-09
Thanks cookies:KS, that sounds more like a solution to this problem! I'll let people know if it works (not near my comp for a few days)

---

