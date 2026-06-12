---
title: "Re install nvidia driver?"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by bossa on 2008-03-21
Hi All
I have been running gutsy with a nvidia 7300GT card with the new nvidia drivers (via synaptic) for some time with no problem.
After re booting my computer earlier I noticed the resolution had changed to 1024x768 . There was no option to go higher in screens and graphics I tried reinstalling the Nvidia new driver from synaptic and on rebooting got an error and could not get into Ubuntu. I ended up doing sudo dpkg-reconfigure xserver-xorg. When back in Ubuntu I tried to install the nvidia new driver but get this error :

E: /var/cache/apt/archives/nvidia-glx-new_100.14.19+2.6.22.4-14.10_i386.deb: trying to overwrite `/usr/bin/nvidia-xconfig', which is also in package nvidia-xconfig

Any advice please?

---

### Post by cotcot on 2008-03-21
You could try [[COLOR="Red"]envy[/COLOR]]("http://www.albertomilone.com/nvidia_scripts1.html") .

---

### Post by herbster on 2008-03-21
Have you tried running "nvidia-settings" ?

---

### Post by bossa on 2008-03-21
Thanks cocot that did the trick :) 
@ herbster I did not have "nvidia settings" installed. There was a no go whan I tried to install it earlier ...same error as the original problem .

---

### Post by forrestcupp on 2008-03-21
> **bossa said:**
> @ herbster I did not have "nvidia settings" installed. There was a no go whan I tried to install it earlier ...same error as the original problem .

If you were using the nvidia-glx-new package, it includes nvidia-settings.  That nvidia-settings package is for the legacy drivers and it won't install with the new drivers because it is already included.  You can find it either in the 'System Tools' part of your main menu, or by typing nvidia-settings in a terminal.

---

### Post by herbster on 2008-03-21
Take note that it is "nvidia-settings" with a dash between the words.

This GUI interface is the best and most user-friendly means for folks to configure their visual settings with an Nvidia card. If you do get it working and like the result, you can hit Save to X Configuration file near the bottom (above the Quit button), but since that's writing to the /etc/X11/xorg.conf file you must use root to do it successfully. Run it as root with

```
gksudo nvidia-settings
```

---

### Post by bossa on 2008-03-21
> **forrestcupp said:**
> If you were using the nvidia-glx-new package, it includes nvidia-settings.  That nvidia-settings package is for the legacy drivers and it won't install with the new drivers because it is already included.  You can find it either in the 'System Tools' part of your main menu, or by typing nvidia-settings in a terminal.

> **herbster said:**
> Take note that it is "nvidia-settings" with a dash between the words.

This GUI interface is the best and most user-friendly means for folks to configure their visual settings with an Nvidia card. If you do get it working and like the result, you can hit Save to X Configuration file near the bottom (above the Quit button), but since that's writing to the /etc/X11/xorg.conf file you must use root to do it successfully. Run it as root with

```
gksudo nvidia-settings
```

Thanks a lot guys I could not find the "nvidia-settings" before, it was never in the menu...well I dont think so ;)

---

