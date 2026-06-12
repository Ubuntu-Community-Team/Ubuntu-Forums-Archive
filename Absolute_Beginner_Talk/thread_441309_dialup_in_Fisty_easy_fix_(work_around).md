---
title: "dialup in Fisty easy fix (work around)"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by Paul Helbert on 2007-05-12
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/94304](https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/94304) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I hacked around for several days after the Fisty distro DVD arrived and had no luck. Had all sorts of problems: pulse reset, DNS not set properly so no web addresses found even when I got the modem working (via wvdial pon/poff), dialing up while booting...you name it I had them all. I even got online with internet connection once for a short while. What a headache!

The easiest solution seems to be install and use gnome-ppp (or kppp if you like). You may need to uncheck the boxes on the wired and modem connections and uncheck the box under modem properties in system>administration>network to get it working, but that's easy and it does work flawlessly and all from the Gnome GUI.

Since gnome-ppp was not on the distro DVD, I had to find it elsewhere. I brought it over on a pen drive as a debian package and installed it. Then after I had things working correctly, I was able to download and install a newer version through Synaptic.

Many others have suggested that the dialup feature in  system>administration>network is broken and that it should be fixed or eliminated. Since the distro DVD users are those of us located far from high speed possibilities, I suspect we will see many others needing help with modem set up as the DVD's are now arriving in the mail.

---

