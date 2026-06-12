---
title: "Ubuntu installs from CD, won't boot"
date: 2005-04-05
forum: Apple PPC Users
---

### Post by PCM2 on 2005-04-05
Well, I've got Ubuntu installed on my G4/733/SuperDrive -- in fact, I installed it twice -- but both times it wouldn't boot. After the first-stage install, if I pull up Open Firmware, it gives me the option to boot from either the Mac OS X or the Linux partition. When I choose the Linux partition I get the yaboot menu. When I hit return, it says it's booting Linux ... but then immediately fails with a message saying my filesystem is either corrupt or not recognized.

I tried installing Ubuntu twice; once with the partition's filesystem set to ReiserFS, then the second time with it formatted as Ext3. The result was the same each time. What else could I be doing wrong?

---

### Post by DJ_Max on 2005-04-05
Wait, did you use OS X disk thing to boot Linux? The first thing that boots should be Yaboot. I've heard that using OS X disk thing to boot into Linux will mess up your Linux install.

---

