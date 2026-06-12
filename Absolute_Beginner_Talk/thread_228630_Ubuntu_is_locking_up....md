---
title: "Ubuntu is locking up..."
date: 2006-08-03
forum: Absolute Beginner Talk
---

### Post by tgdrums1990 on 2006-08-03
Anytime i run terminal and close terminal it locks up, or anytime i run NVU it locks up... Why is this... I figured linux was gonna be stable...

---

### Post by kadymae on 2006-08-03
Is there any error message that could help us help you?

Can you get into the system log (sorry can't tell you how to do that off the top of my head --at work) and see what it says right about the time of the crash?

---

### Post by tgdrums1990 on 2006-08-03
Well when it locks up, it just freeses, and then it dose nuthing, it just sits there. So i hit the reset button a restart and it comes up like nuthing happend.

---

### Post by kadymae on 2006-08-03
After you reboot, go into the System Log (again, I can't tell you off the top of my head where it is, but if you hit the wiki, you should be able to find where to find it. [Also, I'm running Xubuntu, not Ubuntu]) and see what it says about what's happening.

When OS 10.3.5 completely bork'd my PowerMac, examination of the system log gave me several clues as to just exactly how bork'd things were.  (So bork'd that I had to wipe the drive and start over.)

Also, open up Synaptic and look around and there will be an option to repair broken packages.  Run this and see if it fixes any problems.

Finally, when I upgraded from 5.10 to 6.06, my Ubuntu install became hopelessly corrupted, beyond the point of package repair to fix.  I ended up wiping the drive and starting all over.

---

