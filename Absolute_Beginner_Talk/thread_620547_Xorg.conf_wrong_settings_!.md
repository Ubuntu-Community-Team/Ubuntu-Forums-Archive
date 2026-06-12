---
title: "Xorg.conf wrong settings !??"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by pollinn on 2007-11-22
Hi,

I setup Edgy as my primary os this spring, after lots of trouble with my graphics driver, i got it working just fine with emerald and it looked really neat. Anyway, i went on vacation for 4 months this summer. When i come back, i turn on my computer it loads ubuntu and! error message your xorg.conf settings are wrong.. the message is much longer with very ugly blue red and white theme decorated with geiberish characters. 
So it shuts down the x server and i cant do anything.If i load the cd the screen just goes wierd and i can´t make anything out, even in safe graphics mode.

What happened in these four months of my computer being turned off?
Any ways, it sucks to have an os that actually depends on you having a windows partition or a second computer to get fixes for it because it is so unrelyable. 

So my final question on this forum would be.. Is it enough to format the ubuntu partitions to get rid of it? or do i have to get it working  to uninstall it?

---

### Post by Dr Small on 2007-11-22
You could try reconfiguring X server, if you can get to a terminal:
```
sudo dkpg-reconfigure xserver-xorg
```

---

