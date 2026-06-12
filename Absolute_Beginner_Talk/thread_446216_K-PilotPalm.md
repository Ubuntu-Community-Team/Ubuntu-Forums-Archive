---
title: "K-Pilot/Palm"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by Tumpster on 2007-05-16
Hey there, I was running with KPilot today and I'M getting some apparnt errors and it dosen't seem to be sinking up at all. This is what i get: 
16:52:16 Starting the KPilot daemon ...
16:52:16 Daemon status is `not running'
16:52:16 Pilot device /dev/ttyUSB1 does not exist. Probably it is a USB device and will appear during a HotSync.
16:52:21 Device link ready.
16:52:22 Checking last PC...
16:52:22 KPilot 4.6.0 (blivit) HotSync starting...

16:52:22 Using encoding UTF-8 on the handheld.
16:52:22 HotSync is disabled because KPilot could not determine the state of the screen saver. You can disable this security feature by unchecking the 'do not sync when screensaver is active' box in the HotSync page of the configuration dialog.
16:52:22 End of HotSync

16:52:22 HotSync Completed.
16:52:27 Pilot device /dev/ttyUSB1 does not exist. Probably it is a USB device and will appear during a HotSync."

I was curious if anyone is willing to take a look at this and diagnosis it? Thanks!

Craig

---

### Post by Snowmayne on 2007-05-18
<SIGH> I've been getting the same error and when I try to configure kpilot through the menu system, the app freezes and I have to force quit to shut it down.

---

### Post by tgzuke on 2008-06-16
Although this issue is over a year old, I played around with it for a few minutes and, although I didn't cover the root of the problem (that is, why the screen saver status isn't detectable by kpilot and why kpilot locks up when one tries to configure it), I have a solution:

In the terminal,
$ kpilot -s

will open the configure dialog. Click on the HotSync tab, uncheck the screen saver box, and presto! Things work fine.

---

