---
title: "Feisty Broadcom Problems"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by WolfCarinea on 2007-04-22
I downloaded and installed 6.06 onto my computer, upgraded to 6.10 then to 7.04. i have a Compaq Presario R3000Z, with a Broadcom 4306 802.11 b/g wireless card. I DID NOT GET IT WORKING BEFORE I UPGRADED. I have ndiswrapper, installed the drivers bcmwl5.inf bcmwl5a.inf and bcmwl5.sys. The wireless card won't show up when i open Network.  any ideas?

---

### Post by leibowitz on 2007-04-22
With a little search on to the ubuntuforums.org (yes, it's here)

[1] [http://ubuntuforums.org/showthread.php?t=417155](http://ubuntuforums.org/showthread.php?t=417155)
```
sudo ifconfig wlan0 up
```

[2]  Complete how-to: [http://ubuntuforums.org/showthread.php?t=201902](http://ubuntuforums.org/showthread.php?t=201902)

[3] Another installation guide: [http://ubuntuforums.org/showthread.php?t=340689](http://ubuntuforums.org/showthread.php?t=340689)

---

