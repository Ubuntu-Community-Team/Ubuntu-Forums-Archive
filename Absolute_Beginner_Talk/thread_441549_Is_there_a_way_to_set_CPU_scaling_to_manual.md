---
title: "Is there a way to set CPU scaling to manual?"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by RTO on 2007-05-12
hey, im using a acer aspire 1350. the cpu is scaling fine but is kicks into full power mode all the time aka uber loud fan mode.. and well this notebook is abit old and has always ran hot and shuts off. 

in windows ive always sholved this by manually setting my cpu to a power saving mode.

im sure theres a way to do this. just not sure how. is there an applet or something i can use? not to just view the freq but acutally set it. 

thanks 

-RTO

---

### Post by FuturePast on 2007-05-12
```
$ gconf-editor
```
Look for key /apps/gnome-power-manager/cpufreq_ac_policy

---

