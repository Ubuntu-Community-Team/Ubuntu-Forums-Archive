---
title: "Desktop resolution problem on a FPD2485W 24&quot; monitor running under Edgy with a 6800GT"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by seeknowsage on 2007-07-20
The psu and cpu on my primary computer recently died, so I've moved my Ubuntu Edgy machine running on a BFG 6800GT OC over to my main lcd. My ubuntu machine normally runs on a 22" lcd at 1680x1050, but this monitor's native resolution is 1920x1200. I've tried editing the settings of the xorg.conf file manually, by using **sudo apt-get install nvidia-glx-new**, and by the Nvidia Settings program. However, when I attempt to change the resolution up to 1920x1200, the screen becomes "stretched", as shown in the picture below:

[[IMG]http://img408.imageshack.us/img408/6936/screenshotrh1.th.png[/IMG]](http://img408.imageshack.us/my.php?image=screenshotrh1.png)

Is there any way to overcome this so I can run my monitor in the native resolution of this monitor? Furthermore, will I only have to replace the xorg.conf file with a backup when I move it back to my 22" monitor?

---

### Post by Happy_Man on 2007-07-20
Umm.... I suggest you run ```
dpkg-reconfigure xserver-xorg
```

Make a backup of your xorg.conf before you run that, so that your old monitor will work. 

Use spacebar to select, just keep hitting enter until you get to the list of resolutions.

---

### Post by CautionaryX on 2007-07-20
Try changing the refresh rate in nvidia-settings from Auto to the other refresh rates.

---

### Post by seeknowsage on 2007-07-20
I'm sorry, when I bolded the one command line in my original post, I pasted the wrong one. ```
dpkg-reconfigure xserver-xorg
``` is what I ran.

---

