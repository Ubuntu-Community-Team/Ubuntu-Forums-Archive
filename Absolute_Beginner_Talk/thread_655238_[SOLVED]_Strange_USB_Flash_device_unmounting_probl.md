---
title: "[SOLVED] Strange USB Flash device unmounting problems"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by Xavieran on 2008-01-01
When I unmount any USB flash drives a gksudo window comes up asking me for my root password because "for security reasons this disk is restricted to use by sys admins ..." so I type in my password an then it says ...the drive could not be unmounted :cannot remove directory...

---

### Post by metalpancake on 2008-01-01
maybe you could try gparted?

---

### Post by Xavieran on 2008-01-01
I somehow fixed it...I did this mount /dev/sdb /media and wrote over the /media folder ...then when I rebooted (with heart in throat) everything was fine...

---

