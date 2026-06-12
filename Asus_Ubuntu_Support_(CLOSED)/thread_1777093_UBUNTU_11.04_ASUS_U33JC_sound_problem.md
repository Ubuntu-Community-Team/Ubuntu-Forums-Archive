---
title: "UBUNTU 11.04 ASUS U33JC sound problem"
date: 2011-06-07
forum: Asus Ubuntu Support (CLOSED)
---

### Post by acrobaticman on 2011-06-07
Dear all

I am using asus u33jc running a 32bit ubuntu 11.04

and I have no sound at all. 

My sound information is in this link
[http://www.alsa-project.org/db/?f=5e59e2e245a893f59e4ed2bf1d16ae73c6eea61f]("http://www.alsa-project.org/db/?f=5e59e2e245a893f59e4ed2bf1d16ae73c6eea61f")

Please anybody help me.

ps. The sound preference is not mute

---

### Post by lidex on 2011-06-18
Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=hp-laptop" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

---

### Post by condefenring on 2011-08-26
If this help you. I dont have any problem with sound and ubuntu 11.10 32bits
The only issue i can not output HDMI sound.
Someone can help with this issue???

---

### Post by lidex on 2011-08-28
> **condefenring said:**
> If this help you. I dont have any problem with sound and ubuntu 11.10 32bits
The only issue i can not output HDMI sound.
Someone can help with this issue???
Have a look at these:
[http://ubuntuforums.org/showthread.php?t=1615564](http://ubuntuforums.org/showthread.php?t=1615564)
[http://ubuntuforums.org/showthread.php?t=1806896](http://ubuntuforums.org/showthread.php?t=1806896)

---

