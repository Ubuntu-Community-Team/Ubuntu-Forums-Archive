---
title: "Tiny fonts on logon screen"
date: 2007-04-06
forum: Apple Intel Users
---

### Post by danb35 on 2007-04-06
After a bit of tinkering, I have Ubuntu 6.10 installed and running pretty well on my Intel Mac Mini (1.66 Core Duo).  Its main purpose is to be a MythTV box, so it's connected to a Panasonic TH-50PH9UK plasma display via the VGA connection.  My current problem is that, in certain places on the logon screen, the fonts are tiny enough to be unreadable.  The host name, date and time in the lower right corner of the screen are fine, as is the Options menu button in the lower left.  However, the items on the options menu are tiny (I'd guess about 3 pixels high).  Also, when I enter my username to log in, it's equally tiny.

Once I've logged in to my regular GNOME session, everything is fine--all menu items are in readable type, the terminal window is usable, etc.

I'm guessing this is something in my xorg.conf, but I'm not sure what to check.  I tried setting the DPI to 100x100, but that didn't seem to have any effect.  What should I be looking for?

---

### Post by danb35 on 2007-04-07
Well, a little bit of further investigation reveals the fact that X is running at a resolution of 31 x 31 DPI, which seems to me to be a likely reason for the small fonts.  I attempted to correct that by adding

Option "DPI" "100 x 100"

in the Device, Monitor, and Screen sections in xorg.conf, but that resulted only in a log entry that ' Option "DPI" is not used '.  Apparently I need to find some other way to set my monitor DPI in xorg.conf.  I'll keep looking on that, but any suggestions would be appreciated.

---

### Post by danb35 on 2007-04-07
I've now found that I can achieve the desired result by adding

DisplaySize 340 192

to the Monitor section.  I think it'd be cleaner to be able to specify DPI directly, but this seems to be doing the trick right now.

---

