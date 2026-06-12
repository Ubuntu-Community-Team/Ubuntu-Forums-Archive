---
title: "wine uninstaller does not uninstall project64/ audio problems"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by Tuxoid on 2007-08-22
I installed wine to install project64, the audio didn't. I tried several things in winecfg. They are listed below:
---------------------------------------
Hardware Acceleration: Full
Driver Emulation: Off
Bits per Sample: 8
ALSA Checked
Sample Rate: 22050
Results: Audio skips quickly
------------------------------------

-------------------------------------
Hardware Acceleration: Emulation
Driver Emulation: Off/On
Bits per Sample : 16
ALSA Checked
Sample Rate: 44100
Results: Audio skips slowly with either driver emulation setting
-------------------------------------

-------------------------------------
Hardware Acceleration: Basic
(Everything else the as previous settings)
Results: Audio skips fast
------------------------------------

I restart the computer (not a simulated windows restart, restarting Ubuntu) thinking it might fix something, I get back in and load up project64 and once I load my rom, the program shuts down after a few seconds. Tried to run roms a couple more times with the same results and I just decide uninstall project64. I run the uninstaller, everything for the unintaller runs fine; but after the uninstaller runs, I can still run the program (even after repeatedly uninstalling it). I can and have ran the linux version mupen64; but for the rom I'm trying to run, it just won't cut it.

---

### Post by axemurder785 on 2007-08-22
you could always purge wine and then reinstall it....


```
sudo apt-get remove wine --purge
```

---

### Post by Tuxoid on 2007-08-23
I purged it, I'm just running mupen. Thanks.

---

