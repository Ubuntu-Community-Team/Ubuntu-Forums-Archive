---
title: "Default CPU frequency mode?"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by larsdk on 2007-09-03
Hi there,

Since I happen to have a laptop, which is extremely noisy when it's not forced to perform at an absolute minimum, I would like to make Ubuntu start up with "Powersave" instead of the default "On-demand" - any suggestions?

Lars

---

### Post by Kobalt on 2007-09-03
You can determine the CPU policy whether you're on battery or AC from Gconf. Press Alt+F2 and enter *gconf-editor*. Browse in apps, gnome-power-management, cpufreq. Edit the key for *policy_ac* (and maybe *policy_battery* as well) from ondemand to powersave, and your computer will run this mode unless you set it to another one.
Then use the cpufreq applet to change your CPU policy.

---

### Post by larsdk on 2007-09-03
thanks a bunch :)

---

