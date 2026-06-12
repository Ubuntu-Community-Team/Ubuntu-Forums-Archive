---
title: "Screen Resolution"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by reesy on 2007-12-14
I had my screen resolution set to 1280x960 but when i re-booted my computer today it changed its self to 1600x1200. I have compiz-fusion running but when i turned it of and tried changing the screen resolution it still didn't work. If I change the screen resolution and click apply it doesn't change it then and when i click Keep resolution it put's the settings back to 1600x1200. I have a Nvidia Geforce G8400GS graphics card and am running Ubuntu Gutsy Gibbon. I do have the restricted driver running for the Nvidia card. If any one has any suggestions on how to fix the problem i would be grateful.

---

### Post by siciliancasanova on 2007-12-14
Open up this file in the terminal and check it out ```
sudo nano /etc/X11/xorg.conf
```

I had the same problem, with the resolution not sticking when I hit apply.  I just had to go in and manual configure my settings.

---

### Post by reesy on 2007-12-14
Thanks for the help but I just thought i would try restarting my computer one more time and what do you know it went back to normal :S.

---

### Post by siciliancasanova on 2007-12-14
Glad that worked.  Yeah compiz-fusion is a weird one.  You can do what seems to be almost nothing and it craps out on you and like last night I installed Hardy on my root partition and compiz-fusion still works flawlessly.

---

