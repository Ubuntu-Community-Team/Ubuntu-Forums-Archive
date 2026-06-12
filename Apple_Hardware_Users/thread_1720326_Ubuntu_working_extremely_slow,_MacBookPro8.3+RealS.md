---
title: "Ubuntu working extremely slow, MacBookPro8.3+RealSSD"
date: 2011-04-03
forum: Apple Hardware Users
---

### Post by Sasha55 on 2011-04-03
I’ve got a new MacBookPro8.3 17“ + RealSSD C300 256Gb, MacOS+Win7
and now I’m trying to get Ubuntu 10.10 64bit running. Unfortunately it takes ~30min :confused:
to start Ubuntu, and then every access to HDD(SSD)  take really long :confused:. Please help.

---

### Post by Sasha55 on 2011-04-04
Now I’ve got little bit more information, if I start windows (doing reboot, and not shutdown) before starting ubuntu than everything is working. It seems that the problem is on some devices IRQ etc. that are not initialized by ubuntu, or need to be initialized before ubuntu starts.

---

### Post by Sasha55 on 2011-04-06
I found this thread
[http://ubuntuforums.org/showthread.php?t=53227](http://ubuntuforums.org/showthread.php?t=53227)
how can i change to S-ATA from S-ATA/P-ATA?

And I have other problem with win7, the brightness is not working, to solve it i clear NVRAM everytime i reboot: alt+cmd+r+p.

Is there a generic way to change NVRAM setting on macbook? and maybe to save and update them in rEFIt ?

---

### Post by psymin on 2011-04-11
Unfortunately I can't help you, but I would love to know if you are using the binary driver for your video card.  It is called fglrx or Catalyst.  When you use glxgears how many fps do you get?

---

