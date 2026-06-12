---
title: "System locks up, forces restart, cause unkown (x going nuts?)"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by skyhopper88 on 2007-02-21
My specs are as follows:
Ubuntu 6.10
Athlon 64 3400+
1.5 gig RAM
7900GT

I'm not sure what exactly is causing this, but at seemingly random times my system will lock up. My mouse will freeze and I'll be unable to do much of anything. alt tab still switches between windows and some shortcuts work for a time. Restarting x just leaves me with my background but it won't restart. alt sysreq k blurs my entire monitor into stretched lines, so I'm thinking x seems to be messing up big time. After a short while my system just reboots. I'm not sure how to diagnose this, at first I thought it was beryl at fault, but it happens even in plain gnome too. It's happened while I'm just working with a document, checking a dialog box, restarting apps, spinning beryl's cube, returning from screen saver, it seems to have no correlation. I installed the nvidia drivers via envy and have tried uninstalling/reinstalling the drivers with it and from synaptic and reconfiguring xserver several times. I'm not sure what else to try.

---

### Post by skyhopper88 on 2007-02-21
Could envy have messed something up? When I reconfigure xserver it complains about it being customized when I get to color depth and another back up is created. I have tons of em. I guess I'll try uninstalling the driver with envy, reconfiguring x, then getting the driver from synaptic the next chance I get.

---

### Post by skyhopper88 on 2007-02-21
That didn't work, still locked up in gnome.

---

### Post by skyhopper88 on 2007-02-21
Any ideas on what would cause a random lock up like this?

---

### Post by skyhopper88 on 2007-02-22
I promised myself I wouldn't reinstall until Fiesty, and I'd like to keep it. Any advice would be greatly appreciated.

---

### Post by crane on 2007-02-25
Run a memtest at boot.
I had a random system lock up problem that turned out to be memory. It was brand new memory at that.
Be sure to let it run for a while. I let mine run for 6 hours.

---

