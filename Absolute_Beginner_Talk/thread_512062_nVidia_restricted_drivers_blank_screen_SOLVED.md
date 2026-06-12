---
title: "nVidia restricted drivers blank screen SOLVED"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by paradoxchild on 2007-07-28
If you've got the restricted drivers for nvidia, but now for some reason there is no signal (blank screen) at login screen but still the drum noise, this is the answer. (This should be made into a sticky)

Add the following line to the Screen section of xorg.conf

Option    "UseDisplayDevice"   "DFP"

---

