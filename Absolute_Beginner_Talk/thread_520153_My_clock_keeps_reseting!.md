---
title: "My clock keeps reseting!"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by limberlegs on 2007-08-07
My clock should be set to EST (GMT -4), which I set when I installed ubuntu.  It seems that every time I reboot the computer the clock resets to GMT.  I right-click the time and enter my root password and set it back, only to have it reset after the next reboot.  What gives?

---

### Post by zek725 on 2007-08-08
Your CMOS battery probably needs to be replaced.

---

### Post by limberlegs on 2007-08-08
I don't think so.  When the clock resets, it is always to the correct time, just the wrong time zone.  It appears that my timezone settings are not sticking.  Also, I didn't have these problems when I was running XP.  If it was the battery, I imagine I would have had the same problems while running XP.

---

### Post by edwardLS on 2007-08-08
I have had this issue several months ago also.  While I don't understand the suggested fix I received, I do understand that it worked.

I am not at my Ubuntu system right now, so I hope my memory will not fail too bably.

Edit (as sudo) the file: /etc/default/rcS,

Find in that file a line that looks something like: UTC=yes, and change (edit) it to UTC=no.
Save the file and you should be done.

Hope this helps.

---

### Post by limberlegs on 2007-08-08
Cool.  Thanks for the reply.  I'll try it when I get home from work!

---

