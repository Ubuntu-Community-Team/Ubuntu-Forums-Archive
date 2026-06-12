---
title: "Dual screen caused HAL problems"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by rafarquhar on 2007-12-28
So today, I found the "Graphics and Screens" or "Screens and graphics" menu, where you configure dual screens and such.

Being stupid, I assumed it would work without a hitch.  Now, on start up, I get a "HAL failed to initialize" message.  I have tried to put my settings back to the way they were, but to no avail. Even when I get my screen to (apparently) display like it used to, I still get the HAL error. Any help?  I was going to just shrug it off and back up my stuff to a USB drive and start over, but not only is that annoying, but I can't access my USB drive from Ubuntu anymore, but I'm guessing that's just 'cause the HAL issues.  Any help?

---

### Post by blueridgedog on 2007-12-29
Sort of a long shot, but unplug all USB devices and reboot and see if the error persists.

Others with similar problem have suggested disabling autologon:

gksudo gdmsetup

and uncheck automatic login.

---

