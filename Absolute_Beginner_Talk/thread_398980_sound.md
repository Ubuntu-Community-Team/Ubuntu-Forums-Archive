---
title: "sound"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by tlion on 2007-04-01
hello, 

i've got ver 6.06 LTS and I just put this on an older computer running xp.  the computer has sound integrated but it isn't working with ubuntu.  whenever i try to load music or video it says unable to communicate with the sound server.  the system doesn't play sound at login either.  i think that it just needs drivers but I don't know how to do that. 

thanks so much

---

### Post by mills on 2007-04-01
have you tried [this?]("http://www.ubuntuforums.org/showthread.php?t=205449&highlight=sound+problem+aplay")

---

### Post by tlion on 2007-04-01
tried something similar without success but this is more comprehensive.  thanks

---

### Post by tlion on 2007-04-02
turns out that it didn't work either.  

It says that I don't have the correct gstreamer plugins installed.  ??????

thanks

---

### Post by Shinoda on 2007-04-14
Try reinstalling ALSA:```
sudo aptitude purge linux-sound-base alsa-base alsa-utils
sudo aptitude install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop
```(replace [FONT=Courier New]ubuntu-desktop[/FONT] with [FONT=Courier New]xubuntu-desktop[/FONT] if you're running Xubuntu) and reboot.

Alternatively follow e.g. [these]("http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide#ALSA_driver_Compilation") instructions to compile it yourself.

---

