---
title: "Screen Resolution"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by SniperClops on 2007-07-05
Greetings,

I just installed Ubuntu and used the NVIDIA drivers but I am stuck at 800x600 resolution and 50 Hz refresh rate... and it sucks. How do I change my resolution? I went to System->Preferences->Screen Resolution but the only option is 800x600, 50 Hz.

---

### Post by AlexenderReez on 2007-07-05
have you installed Nvidia driver ....setting to use Nvidia card ...the i get  1024 * 768 and refresh rate 50hz ..... the highest refresh rate is 54 but i use default ....it is seems great i stick with 50hz

---

### Post by mjwhitfield on 2007-07-05
```
dpkg-reconfigure xserver-xorg
```

that should give you all the beans.

---

### Post by nitro_n2o on 2007-07-05
There are so many posts about screen resolution (I personally maybe have more than 2) I think you'll be able to fix it by search the forums... but you can also post  your xorg.conf file so someone can tell wht's going on... 
yeah 800x600 sucks!!!

---

### Post by scxtt on 2007-07-05
you need to add VertRefresh & HorizSync [specific to your monitor] to the "Monitor" section of your /etc/X11/xorg.conf ...

---

### Post by alienexplorers on 2007-07-05
If you have the nvidia drivers running then nvidia-settings should be running.  You could use that to change some of the setttings.  You can also use the following lines in your xorg.conf to change resolution and refresh rates:
> Section "Monitor"
    Identifier     "Monitor0"
    HorizSync       28.0 - 70.0
    VertRefresh     43.0 - 120.0
    ModeLine       "1280x1024_65.00" 119.4 1280 1368 1504 1728 1024 1025 1028 1063 -hsync +vsync
    Option         "UseEdidFreqs" "FALSE"
    Option         "UseEDID" "FALSE"
    Option         "DPMS"
EndSection


The modeline can be found at [http://www.sh.nu/nvidia/gtf.php](http://www.sh.nu/nvidia/gtf.php)

---

### Post by SniperClops on 2007-07-05
> **alienexplorers said:**
> If you have the nvidia drivers running then nvidia-settings should be running.  You could use that to change some of the setttings.  You can also use the following lines in your xorg.conf to change resolution and refresh rates:


The modeline can be found at [http://www.sh.nu/nvidia/gtf.php](http://www.sh.nu/nvidia/gtf.php)

Where do I find nvidia-settings, I checked my menus but can't find it.

---

### Post by SniperClops on 2007-07-05
> **mjwhitfield said:**
> ```
dpkg-reconfigure xserver-xorg
```

that should give you all the beans.

Did that but didn't change anything

---

### Post by sab0403 on 2007-07-05
In my experience with the nVidia driver, you have to add the Vertical Refresh and Horizontal Sync specifications for your monitor, yes, but also you have to add something else to your xorg.conf file (in the "Device" section): ```
Option "UseEDID" "False"
```

Also, you might have to change the way the resolutions are expressed in the "Screen section". For instance, instead of: ```
 SubSection "Display" Depth 24 Modes "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480" EndSubSection
``` you might want to put: ```
 SubSection "Display" Depth 24 Modes "1280x1024_75" "1024x768" "832x624" "800x600" "720x400" "640x480" EndSubSection
```

Where the number after the _ is refresh rate you want for that particular resolution. Be careful with this - your monitor and your card HAVE to support it.

Credit to [this guide]("http://www.albertomilone.com/latest_nvidia_udsf_feisty.html") (step 10, Problems section).

---

### Post by sab0403 on 2007-07-05
BTW, adding the horizontal sync/vertical refresh is easy. Go to the "Monitor" section on the xorg.conf file and add: ```
HorizSync      28-61
VertRefresh    48-75
```

Of course, those numbers have to fit your monitor. Google your monitor's model and "vertical refresh" or "horizontal sync" and you'll find it.

---

### Post by SniperClops on 2007-07-05
I am going back to Mandriva for now, everything just works out of the box for me. I'll give Ubuntu another try when the next version is released.

---

