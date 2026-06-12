---
title: "Can't Change Back To Default Theme"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by SamTyson92 on 2007-11-08
I've just tried a Emerald Theme and now I can't get back to the default Gnome skin.
I've removed the Emerald Theme by clicking delete and trying to click on the default skin in Appearance but I've tried rebooting, logging off and shutting down and back up and it still won't go back.
How can I get it back to normal?

---

### Post by inversekinetix on 2007-11-08
> **SamTyson92 said:**
> I've just tried a Emerald Theme and now I can't get back to the default Gnome skin.
I've removed the Emerald Theme by clicking delete and trying to click on the default skin in Appearance but I've tried rebooting, logging off and shutting down and back up and it still won't go back.
How can I get it back to normal?


I've been trying to do the same thing for a week, no one seems to know.  I'm supposed to have a 'theme' setting in my compiz manager but there isnt anything.  BTW what happened after you uninstalled emerald?

---

### Post by qamelian on 2007-11-08
To switch back to a "non-emerald" theme, press alt-F2 to get the Run Application box. In the box, type: ```
gtk-window-decorator --replace
```and press enter. This tells Ubuntu to go back to using the default Gnome decorator for drawing window themes.

---

### Post by SamTyson92 on 2007-11-09
> **inversekinetix said:**
> I've been trying to do the same thing for a week, no one seems to know.  I'm supposed to have a 'theme' setting in my compiz manager but there isnt anything.  BTW what happened after you uninstalled emerald?

I haven't unistalled emerald I followed the above meathod but it just changes back after a re-login or reboot so is uselss unless you remove Emerald I guess.

---

### Post by inversekinetix on 2007-11-09
thanks for the reply

---

### Post by qamelian on 2007-11-11
> **SamTyson92 said:**
> I haven't unistalled emerald I followed the above meathod but it just changes back after a re-login or reboot so is uselss unless you remove Emerald I guess.

The script /usr/bin/compiz tests to see if you have emerald installed. If emerald is found, it gets used by default.

If you don't want to uninstall emerald, you can either edit /usr/bin/compiz (the potentially dagerous option!) or you can go to System > Preferences > Sessions and add an item to your startup. The command ```
gtk-window-decorator --replace
``` added to your startup should cause the original decorator to replace emerald when you login.

---

### Post by DutyDuty on 2007-11-11
Alternately, type ```
metacity --replace
``` into terminal.

---

### Post by qamelian on 2007-11-11
> **DutyDuty said:**
> Alternately, type ```
metacity --replace
``` into terminal.

Not if you want to continue using compiz. WHat you have just done is turned off desktop effects by replacing compiz with metacity.

---

