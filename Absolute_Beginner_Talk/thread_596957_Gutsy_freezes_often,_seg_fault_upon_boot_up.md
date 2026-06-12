---
title: "Gutsy freezes often, seg fault upon boot up"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by AncientPC on 2007-10-30
Alright, I've run memtest and it's passed 5+ times.  The laptop (Dell Inspiron 6000) dual boots and runs just fine in WinXP.  However when I boot into Ubuntu with just Nautilus, Compiz, and Pidgin running the system will freeze (typically within 30 minutes) and I'm not sure why.

How do I diagnose this problem?

---

### Post by RodM on 2007-10-30
My PC would also freeze regularly after install.  The install had to be done using the acpi=off option for the computer to load at all without a segmentation fault (alternative installer esc,enter, install acpi=off). Looking at the system logs I noticed an apm problem (apmd proxy exited with status1 - apmd standby rejected - apmd standing by now) before each freeze/crash. No session/service reconfiguration would solve the problem so as a fix I have done:  terminal  cd /usr/sbin  sudo mv apmd apmd1. This renaming of the file can obviously be reversed if the fix does not help or a proper correction turns up (sudo mv apmd1 apmd).

Now my PC runs perfectly - I do not know if this will help but good luck.

---

### Post by RodM on 2007-10-30
I forgot to mention that after the fix you have to restart the computer or the PC will still lock-up.

---

### Post by AncientPC on 2007-10-30
Bump, why can't I get even ~30 minutes uptime with Ubuntu before it freezes but WinXP works just fine?  What should I be checking to diagnose this error?

---

### Post by urk_nono on 2007-11-01
Have exactly the same problem. I even did a fresh install since the dist-upgrade failed.

---

