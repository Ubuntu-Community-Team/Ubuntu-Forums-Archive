---
title: "Ubuntu is locked up from installing mouse theme!"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by jondecker76 on 2007-03-01
I installed a mouse pointer theme from gnome-look and now ubuntu is locked up - just after login screen the startup scripts load it just freezes solid.. Logging into a fail safe session, i get an error that there is a problem starting the GNOME settings daemon. How can i fix this?

thanks,
Jon

---

### Post by igknighted on 2007-03-01
Hmm, if you can in failsafe mode, delete the folder related to that mouse theme from /home/username/.icons.  Otherwise, boot into recovery mode to delete it.  That should clear it up.

---

### Post by Dr. Nick on 2007-03-01
Gnome setting daemon will never start in failsafe, it can be the cause of some crashes hence not loaded in "failsafe" . Just use failsafe and delete the offending fiies

---

