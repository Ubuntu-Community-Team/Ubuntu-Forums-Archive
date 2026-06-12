---
title: "[SOLVED] Gutsy - shut down hanging"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by freddybob on 2007-10-21
In Gutsy when I click the red shut-down button in the top-right it takes 45-60 seconds for the "Suspend, Hibernate, Restart, Shut Down" dialog to appear.  Until it appears the system hangs - I can move the mouse cursor but cannot click anything.

Not a serious problem but having to wait 60 seconds quickly becomes annoying.

When the dialog does finally appear and cancel the shut-down, subsequent clicking of the red button brings the dialog up without delay.

I have Desktop Effects turned off.

Any ideas what might cause this?

**D'oh! Just worked out what it is. In the Sessions panel I had stopped the *Power Management Daemon* from running at start-up (I thought that was just for laptops).**

---

