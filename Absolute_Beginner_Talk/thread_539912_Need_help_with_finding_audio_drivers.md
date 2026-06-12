---
title: "Need help with finding audio drivers"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by silverace99 on 2007-08-31
Hi, I'm new to linux and I want to install a audio driver so I can get sound working. My onboard sound card is built by realtek.

My biggest problem right now is that I don't know where to look for linux drivers such as this. Are they readily available? Are they perhaps stored in a repository somewhere? 

Looking at other threads it seems like it shouldn't be this hard...

---

### Post by 5-HT on 2007-08-31
Most available drivers are bundled along with the kernel. You may already have the driver on your system but the device may not be autodetected properly for the module to automagically load. Best thing is to search around to see a) which driver you need and b) if it's already on your system (modprobe -l will come in handy for that). Once you've determined the proper module, add it's name to /etc/modules to have it load on boot.
cheers,

---

