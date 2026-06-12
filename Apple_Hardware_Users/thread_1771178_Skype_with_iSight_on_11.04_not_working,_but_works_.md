---
title: "Skype with iSight on 11.04 not working, but works in cheese"
date: 2011-05-30
forum: Apple Hardware Users
---

### Post by jamesjenner on 2011-05-30
G'day all,

I have 11.04 running very nicely on my 5,1 MacBook, including the iSight. I've tested it via cheese and via web based flash stuff and it seems to work all okay.

I've found however that while skype detects the camera and lets you select it, it doesn't work.

Google has been no joy, in the wild or on these forums. I did find that there was a problem quite a few years ago (around 2007) about Skype support for UYVY but other than that I cannot see anyone reporting a problem. Back then they installed a beta, but considering the age of the post I suspect that will not be a solution for me.

Anyone got any ideas? It's so bizarre. 

:edit:

Skype version is 2.2.0.25 (Beta)

---

### Post by dentament on 2011-08-19
Same problem here with macbook 5,2 and ubuntu 10.04

---

### Post by erLin on 2011-12-13
same problem at my MBpro 2.2 
already any suggestions for fixing? isight + ubuntu + skype?

---

### Post by dentament on 2011-12-13
On 10.04, I have isight not working in skype (it is detected, but only shows one still image) unless I unblock bluetooth
```
sudo rfkill unblock bluetooth
```

---

### Post by mackaframa85 on 2011-12-18
Try mounting the Mac's drive while in ubuntu and install and run isight-firmware-tools from the software center or synaptic if available.  This did the trick for me but I'm running 11.10 and still cannot record video but it works in skype.

---

