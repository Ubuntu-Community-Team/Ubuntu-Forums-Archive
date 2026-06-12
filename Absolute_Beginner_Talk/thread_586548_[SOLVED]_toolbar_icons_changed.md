---
title: "[SOLVED] toolbar icons changed"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by axamax on 2007-10-22
Dell Dimension2300 1.8Ghz, 1GB Ram Just upgraded to Gutsy Gibbon from Fiesty fawn.


I just rebooted my pc after it failed to resume from locked screen. I had an error message about Gnome settings daemon hadn't worked and it would try next start. I noticed that the taskbar icons had changed. The power button had become a green man and most of the other icons on the taskbar and in the applications menu had changed to some extent.
I restarted the computer and the normal appearance had returned.
Where did these other icons come from? Why would they have changed.

---

### Post by ThrobbingBrain66 on 2007-10-22
The gnome-settings-daemon failed to start...that's where the icons came from.  When the g-s-d fails to start it falls back to defaults including the gnome icon theme which you'll see has a green man for the logout icon.

If that ever happens again, hit Alt+F2 and type gnome-settings-daemon into the box and everything will return to normal...no need for a restart.

---

### Post by axamax on 2007-10-22
Ok thanks. I thought it might have been part of the 7.10 upgrade that didn't complete before.

---

