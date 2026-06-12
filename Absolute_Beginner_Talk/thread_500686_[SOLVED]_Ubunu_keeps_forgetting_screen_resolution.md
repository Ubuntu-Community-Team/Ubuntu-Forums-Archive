---
title: "[SOLVED] Ubunu keeps forgetting screen resolution"
date: 2007-07-14
forum: Absolute Beginner Talk
---

### Post by NCAANFI on 2007-07-14
I want to use a screen resolution of 1360x768. Ubuntu  7.04 picks it up and I apply it. But after every reboot it goes to 800x600. I've seen this thread [http://ubuntuforums.org/showthread.php?t=58709&highlight=applying+screen+resolution](http://ubuntuforums.org/showthread.php?t=58709&highlight=applying+screen+resolution) but is there any other way other than deleting resolutions in xorg.conf 

I have the nvidia drivers installed and working properly (7300gt)

---

### Post by bodhi.zazen on 2007-07-14
If you are using the nvidia driver, open a terminal and enter :

```
gksu nvidia-settings
```

Set the resolution/etc you like, then click the "save xorg.conf" button (I forget the name)

No manual edit to xorg.conf is required, but if you run that program as a non-root user you can not save yoru settings (as you can see).

---

### Post by NCAANFI on 2007-07-14
Ahh brilliant.  was wondering WTF was going on. thanks fixed my two probs ejecting USB drives and screen res tonight. Now to fix DVB-T

---

