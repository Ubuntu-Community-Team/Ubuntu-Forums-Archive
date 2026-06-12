---
title: "No volume control GStreamer plugins and/or devices found."
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by Ripfox on 2007-04-11
I am on Ubuntu 6.10 and today my sound broke after an update...

How do i boot to the old kernel in the meantime?

---

### Post by Shinoda on 2007-04-14
Try reinstalling ALSA:```
sudo aptitude purge linux-sound-base alsa-base alsa-utils
sudo aptitude install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop
```(replace [FONT=Courier New]ubuntu-desktop[/FONT] with [FONT=Courier New]xubuntu-desktop[/FONT] if you're running Xubuntu) and reboot.
 
 Alternatively follow e.g. [these]("http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide#ALSA_driver_Compilation") instructions to compile it yourself.

As for booting to other kernels, assuming your [FONT=Courier New]menu.lst[/FONT] is up-to-date (if it's not, [FONT=Courier New]sudo update-grub[/FONT]), hit Escape while GRUB is displaying a countdown before the Ubuntu logo comes up.

---

### Post by Ripfox on 2007-04-14
Thank you, i recompiled alsa a few days ago, and sound works again. One interesting thing i noticed is that .13 works better with my hp dv6000 because it allows me to use aoss with audacity and with the newest alsa, it broke my microphones...hmmm...oh well as long as it works with the older version it's ok with me!

Ripfox

---

