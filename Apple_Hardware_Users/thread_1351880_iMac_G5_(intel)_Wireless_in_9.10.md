---
title: "iMac G5 (intel) Wireless in 9.10"
date: 2009-12-11
forum: Apple Hardware Users
---

### Post by Alexstre on 2009-12-11
Hello!

I ran 9.10 from the Live CD and as soon as it finished booting a popup showed up saying something about property drivers needing to be activated for my wireless card, so I activated the 2 options and everything went fine. I completed the HD install and rebooted, expecting to have the same window show up but it didn't.

Now I'm been looking around trying to figure out where to find those drivers again but I couldn't find anything... so I'm a bit confused.

Anyone knows what I'm talking about? Thanks!

FIXED: I manually downloaded the Broadcom STA wireless drivers as a debian package and installed that. Works like a charm now!

---

### Post by linuxopjemac on 2009-12-11
Under administration there is a tab "Hardware drivers". Start it and select your proprietary driver.

---

### Post by Alexstre on 2009-12-11
> **linuxopjemac said:**
> Under administration there is a tab "Hardware drivers". Start it and select your proprietary driver.

I found this earlier, unfortunately the Hardware Drivers window is empty. It's as if it isn't recognizing that I even have hardware that needs an extra driver! Weird thing is, it worked fine from the Live CD..!

Thanks

EDIT: Actually, after a couple reboots it now display the bwcutter (or whatever it's called) in the drivers window. There's an error when I try to activate it though: something about ArchivesInstall() failing. Time to google about it!

---

