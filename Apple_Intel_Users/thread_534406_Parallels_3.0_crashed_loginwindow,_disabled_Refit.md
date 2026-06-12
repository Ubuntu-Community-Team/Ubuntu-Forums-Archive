---
title: "Parallels 3.0 crashed loginwindow, disabled Refit?"
date: 2007-08-25
forum: Apple Intel Users
---

### Post by Halsnalle on 2007-08-25
I just updated Parallels Desktop to 3.0, build 4560 (MacBook Pro C2D, Mac OS X 10.4.10). Two strange things happened:

* Loginwindow does not answe, according to Process Control, and I can't access Accounts in System Prefs.

* Startup completely bypasses the Refit screen where I used to be able to choose between Mac OS X and Ubuntu 7.04.

Any ideas on how to fix these issues?

---

### Post by cyberdork33 on 2007-08-25
> **Halsnalle said:**
> I just updated Parallels Desktop to 3.0, build 4560 (MacBook Pro C2D, Mac OS X 10.4.10). Two strange things happened:

* Loginwindow does not answe, according to Process Control, and I can't access Accounts in System Prefs.

* Startup completely bypasses the Refit screen where I used to be able to choose between Mac OS X and Ubuntu 7.04.

Any ideas on how to fix these issues?

Just reinstall refit. It is still there, it just needs to be reblessed. Honestly, I don't see a connection between the login window and parallels.

---

### Post by Halsnalle on 2007-08-28
Actually, trashing the prefs for loginwindow (/Library/Preferences/com.apple.loginwindow.plist) solved both problems.

---

### Post by cyberdork33 on 2007-08-28
> **Halsnalle said:**
> Actually, trashing the prefs for loginwindow (/Library/Preferences/com.apple.loginwindow.plist) solved both problems.

Glad you got it working.

---

