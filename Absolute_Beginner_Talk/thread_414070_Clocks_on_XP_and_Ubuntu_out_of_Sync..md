---
title: "Clocks on XP and Ubuntu out of Sync."
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by F_r_e_d on 2007-04-19
Can someone please help?

I have two hard drives in my rig --  One has only XP, and the other has only Ubuntu.  When I set the time correctly on one operating system, it throws it way off on the other (like by 4 or 5 hours or so).

Does anyone know how I can get XP and Ubuntu to stay on the same time?

Thanks in advance.

---

### Post by oilchangeguy on 2007-04-19
make sure both xp and ubuntu are set to get time updates from the internet. this should solve your problem.

---

### Post by lamalex on 2007-04-19
figure out which one is wrong and why? is xp or ubuntu set to the right time zone? sync to an ntp server on both and see if you still have the problem.

---

### Post by starcraft.man on 2007-04-19
I had this happen to me before too... when you installed there is a section when it asks you to install UTC (in text mode I believe, not sure about gui it might not ask). The problem is due to the fact that windows only uses local time and ubuntu defaults to UTC... all ya need is to modify a single line so its UTC= No. Its clearly indicated on this [page. ]("https://answers.launchpad.net/ubuntu/+question/2939") That should do it, that should be it have a nice day.

---

