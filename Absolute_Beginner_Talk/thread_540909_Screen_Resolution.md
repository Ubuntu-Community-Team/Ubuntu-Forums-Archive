---
title: "Screen Resolution"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by Emeric Wood on 2007-09-02
I have a GForce 7600 GS and a 19" TFT, and I only seem to be able to set my resolution up to 1024 x 768. I'd like to be able to set it up to 1200 x (900?). Is there some driver I'm missing or something? I had it set to the 1200 resolution on Windows before I switched over.

---

### Post by Compyx on 2007-09-02
Find out what horizontal and vertical frequencies your monitor can handle and put those in /etc/X11/xorg.conf.

You can do this manually or use:
```

sudo dpkg-reconfigure -phigh xserver-x11

```

---

### Post by kellemes on 2007-09-02
See if this works..

[http://ubuntuforums.org/showthread.php?t=301499]("http://ubuntuforums.org/showthread.php?t=301499")

---

### Post by PmDematagoda on 2007-09-02
Goto Nvidia Settings by opening up a terminal and typing ```
sudo nvidia-settings
```, then goto X server Display Configuration, make the necessary changes and save them to the X configuration File, now see if the resolutions can be taken.

---

### Post by Gone fishing on 2007-09-02
If you are using the nv drivers rather than the nvidia drivers you may first wish to install the nvidia drivers. Download and install the drivers (nVidia glx) using synaptic and then enable them

System > Administration > Restricted Devices Manager
Enable Driver
Apply Changes

then if you can't select the resolution you want you may need to modify your xorg.conf file by adding the resolution in screen section.

---

### Post by Emeric Wood on 2007-09-02
I found out the native resolution's 1280x1024.

After abit of faffing about I installed the Nvidia glx driver, then edited the resolution through sudo nvidia-settings.

Thankyou everyone :)

---

