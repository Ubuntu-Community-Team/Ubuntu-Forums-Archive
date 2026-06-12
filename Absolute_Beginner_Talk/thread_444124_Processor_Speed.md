---
title: "Processor Speed"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by Lindworm on 2007-05-15
Whilst Windows was being a pain in the butt and my hard drive was playing up, in the settings at startup I reset my processor speed to 1500 mhz because it was put to what was safe or something. How can I put it back up to 1800 mhz. 

P.S It runs at 2400 mhz apparently but that wont work on my pc. Too much I think.

Thanks,
Ben

---

### Post by Kobalt on 2007-05-15
Did you set this out in bios ? If so then you should look into this...
You can add an applet to the Gnome panels called CPU monitor : right-click on one of your panels and click Add to the panel. Scroll down to System and settings and double-click on the CPU applet. Now you can see which frequency your cpu is runing at. But you can also act on this frequency if you'd like, in order to set it up or selecting a profile (powersave, ondemand, ect.). To do this open up a Terminal and enter ```
sudo dpkg-reconfigure gnome-applet
```
It will ask you if you should run the CPU applet with root rights, answer yes, and now you're able to manage your cpu frequency from your Gnome panel.

---

