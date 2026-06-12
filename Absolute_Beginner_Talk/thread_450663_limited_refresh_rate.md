---
title: "limited refresh rate"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by Yourdogsdead on 2007-05-21
I just bought a new LCD tv which has a PC Input. When i went to plug it in it said Mode not supported. I quickly figured out that the TV only support a PC input of 60Hz. I can't change the settings , it only gives me the option of 85HZ. how do i open more options up?

---

### Post by Happy_Man on 2007-05-21
If you have a nvidia card.... 
```
sudo apt-get install nvidia-glx
sudo nvidia-settings
```

Or if not....
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by xhilyn on 2007-05-23
Hiya. Thanks for that it just solved my problem and showed me how to get the Nvidia settings control panel up. Is there anyway to make it show under System Preferences? Thanks. xhi.

---

