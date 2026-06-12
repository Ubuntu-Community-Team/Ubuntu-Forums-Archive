---
title: "Battery Monitor not working when Upgraded to 11.10"
date: 2011-10-15
forum: Asus Ubuntu Support (CLOSED)
---

### Post by MrSchism on 2011-10-15
My system, in last fully functional perameters, was as follows:

Kubuntu 11.04 with LXDE installed (I like the KDE Suite and LXDE extended my battery life by an hour and a half).

I had NM-Applet installed as the network manager andI had a battery monitor on my panel.

In upgrading to 11.10, the NM-applet first was overwritten by Network-Manager-Gnome.  I removed that and got NM-Applet to come up.  Twice.  When I stopped one via system manager, both vanished.  Upon rebooting, neither were usable and I was stuck using Network Status Monitor.  NM-Applet is not available any longer, for some reason.

Tolerable, but not my favorite.

Then I noticed my battery monitor was missing from my panel.  I added it back on and it's permanently saying 100% (does not give a drain time).  On charging, it permanently says 100%, but gives a time until charged.  As you can imagine, this is a major issue for a person with a laptop.

I'll be trying the KDE Plasma Netbook interface (ew, I must add) to see if I can get the battery monitor to work there.  I'll post the results here.

---

### Post by MrSchism on 2011-10-15
Well, although I thought the issue may have been the way the OS communicated ACPI information to the monitor panel item, it seems that it's the panel item itself that somehow got broken; The information is correct in KDE Plasma Netbook's battery monitor.  I'll have to figure out how to get that onto the panel.

I'd appreciate any suggestions.

---

### Post by vldmrrr on 2011-10-19
Same problem here. Also noticed that a message on top of the screen appeares for a brief moment during kde startup. Something about KDE power - can not read, goes away too fast. Anyone knows if there is a log of kde messages somewhere?

---

### Post by trooperchix on 2011-11-21
Same problem here.  It's odd though, I noticed that I can run only with the power cord connected.  The monitor is stuck at 16% and my battery isn't charging.  It doesn't make sense that I can run the computer using the cord port, so I'm guessing a program issue here.  Somehow, it the upgrade, my laptop lost the ability to charge batteries and the battery monitor is no longer reads accurately.  Help?

---

### Post by vldmrrr on 2011-11-22
For me the problem was gone after kde 4.7.2update

---

### Post by trooperchix on 2011-11-23
> **vldmrrr said:**
> For me the problem was gone after kde 4.7.2update

How do I figure out what version I'm running?  This problem occurred as soon as I did the upgrade from 11.04 to 11.10.  Everything was peachy before then..  Thanks ahead of time for your help.  :D

---

### Post by vldmrrr on 2011-11-26
> **trooperchix said:**
> How do I figure out what version I'm running?  This problem occurred as soon as I did the upgrade from 11.04 to 11.10.  Everything was peachy before then..  Thanks ahead of time for your help.  :D

You could find version of kde platform by selecting "Help->About KDE" in any kde application, like Dolphine. Platform version is right on top.

---

### Post by jteague48 on 2011-12-13
installed Jupiter on asus eee pc 701.  fixed the battery monitor problem.

---

