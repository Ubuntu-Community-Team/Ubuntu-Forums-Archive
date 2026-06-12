---
title: "How to install ATI x700 drivers with Ubuntu 7.04 X.Org 7.2"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by Ramificatio on 2007-05-05
I have a notebook with ATI X700 GPU. I have downloaded the X700 Linux driver from ATI. When I run the installation however I get a message that the drivers will only install under XFree86 4.3 and X.Org 6.7, 6.8, 6.9, 7.0, 7.1. How do I solved this when I run Ubuntu 7.04 with X.Org 7.2? I have tried and search for a solution but nothing have worked so far or I have no clue of how to go about some suggestions since being a total newbie when it comes to Linux.

 I really want to be able to leave windows behind... fingers crossed.

---

### Post by sloggerkhan on 2007-05-05
I just use regular ATI Linux driver from repos and it works....
The one from restricted driver manager....

---

### Post by Ramificatio on 2007-05-05
> **sloggerkhan said:**
> I just use regular ATI Linux driver from repos and it works....
The one from restricted driver manager....


How do I do this?

---

### Post by DSn0wMan on 2007-05-05
Under the System menu there should be a restricted drivers manager. Just click on that. I also find that the open source drivers work better for my Lappie with the ATI X300 chipset.

---

### Post by Ramificatio on 2007-05-05
> **DSn0wMan said:**
> Under the System menu there should be a restricted drivers manager. Just click on that. I also find that the open source drivers work better for my Lappie with the ATI X300 chipset.

Thanks, Is there a way to test if the drivers works properly with 3D after this is done? Also my notebook has a native resolution of 1280x800 but I can only select up to 1024x768. Is there a fix for this?

---

### Post by DSn0wMan on 2007-05-05
After everything is set up type ```
glxgears
``` at the prompt.

To change your resolution you shoud reconfigure your xserver
1) backup your configuration ```
 sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf .bak
```
2) change your xsettings ```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Ramificatio on 2007-05-05
4138.525 FPS so I guess 3D acceleration is enabled. And I got native resolution. Thanks again!

---

### Post by sloggerkhan on 2007-05-05
Yeah, with ATI, there are real +/- tradeoffs to open vs. closed drivers. My x700 gets somewhat better performance on proprietary and also won't work w/ 3-D games in wine w/o it, but the open driver works much more conveniently with beryl and supports many more screen resolutions.

---

