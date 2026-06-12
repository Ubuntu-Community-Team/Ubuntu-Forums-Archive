---
title: "Kubuntu Power Manager Notifications"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by ackey on 2008-01-09
My laptop (System76 Darter Ultra 2) has some sever power management problems, all known bugs.  Basically, power management programs suddenly can't tell how much power the battery has, etc.  

I recently switched from Ubuntu (Gutsy) to Kubuntu (Gutsy).  Whenever the power manager gets confused (which can be on the order of every 20 seconds) it pops up a message telling me something about being plugged or unplugged, none of which is true or relavent.  The pop-ups are driving me nuts!  I can't find any way to configure the power manager to NOT have them (which would be ok).  So my questions are:

1) Can I turn off the notifications?  How can I do that?
2) What is the best way to implement a different power manager if it is NOT possible to turn off the notifications?  

Just to clarify, the power manager seems to be (from ps):
/usr/bin/python /usr/share/python-support/kde-guidance-powermanager/guidance-power-manager.py

---

### Post by luisromangz on 2008-01-09
You could modify that python script (I know, this is less than optimal) so it wouldn't launch the popup.

You can also remove the kde-guidance-powermanager package, and install kpowersave instead. KPowersave notifications can be easily configured through kde's statandard notifications manager.

---

