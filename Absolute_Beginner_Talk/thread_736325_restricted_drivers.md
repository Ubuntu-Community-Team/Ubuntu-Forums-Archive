---
title: "restricted drivers??"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by SunnyRabbiera on 2008-03-26
certain hardware is listed as restricted as they dont have any open source drivers for linux.
is your system working though? if you are not getting any unusual errors like screen malfunctions then you should be fine, just remember that even though ubuntu is very good with hardware it sometimes blacklists certain hardware due to issues.
if your system is running fine then you should not worry, however if you are trying to run desktop effects this could be a problem.

---

### Post by Charcoal1981 on 2008-03-26
bcm43XX-fwcutter is in the universe repository, which is not enabled by default. Go to "System > Admin > Software Sources" and make sure that the universe repository is ticked active then try the restricted driver manager again.

(This is of course assuming that you decide you do actually need the restricted driver for your wireless card - if it works without I'd leave it like SunnyRabbiera suggests)

---

