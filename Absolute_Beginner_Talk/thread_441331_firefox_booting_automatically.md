---
title: "firefox booting automatically?"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by Roasted on 2007-05-12
Whenever I boot up ubuntu it gives me an error saying firefox failed to launch, yet I never clicked on the icon.

What gives?

---

### Post by heimo on 2007-05-12
Check that it's not included in startup programs under System->Preferences->Sessions. Remove it from Startup programs and Current session -> Apply -> Close.

If it's not there, I have no idea. :)

---

### Post by alienexplorers on 2007-05-12
Check system>preferences>sessions and look at the current session page to see if Firefox is listed if so delete it.  Then go to session options and make sure Automatically save changes to session is checked.  Reboot and see what happens.

---

### Post by Roasted on 2007-05-12
Under the startup programs tab under sessions, I have the following listed.


update-notifier
/usr/lib/evolution/2.8/evolution-alarm-notify
gnome-power-manager
gnome-volume-manager --sm-disable
beagled

---

### Post by alienexplorers on 2007-05-12
What is listed under current session, not startup programs.

---

