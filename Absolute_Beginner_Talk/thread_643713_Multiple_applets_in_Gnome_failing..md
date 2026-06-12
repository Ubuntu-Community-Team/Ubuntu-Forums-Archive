---
title: "Multiple applets in Gnome failing."
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by skogsbær on 2007-12-18
I recently had to run fsck manually, and it looked like it fixed some problems. After rebooting and logging in again, several applets failed and I received this error:

The panel encountered a problem while loading "OAFIID:GNOME_ClockApplet".

Do you want to delete this applet from your configuration?
-

Same thing happened with NotificationAreaApplet, WorkspaceSwitcherApplet, WindowListApplet and ShowDesktopApplet.

Has anyone encountered the same problem?

---

### Post by Severun on 2007-12-18
I saw this happen after I had a hang w/ my fglrx driver and the desktop decided it wanted to restart itself.

After re-booting, then changing my session to "Failsafe Gnome" when I logged in, the problem went away.

---

