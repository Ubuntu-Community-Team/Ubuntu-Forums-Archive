---
title: "Custom resolution shifted to the left?"
date: 2014-01-07
forum: Any Other OS
---

### Post by nholloway2007 on 2014-01-07
I have a laptop running Crunchbang Linux (based on Debian) running Gnome Shell connected to a Samsung SyncMaster B2030 monitor via VGA. It wouldn't display at the monitor's native resolution, so I created a custom resolution using cvt and xrandr as follows: 

```
nickolas@nickolas-crunchbang:~$ cvt 1600 900 60
nickolas@nickolas-crunchbang:~$ xrandr
nickolas@nickolas-crunchbang:~$ xrandr --newmode "1600x900_60.00"  118.25  1600 1696 1856 2112  900 903 908 934 -hsync +vsync
nickolas@nickolas-crunchbang:~$ xrandr --addmode VGA1 
nickolas@nickolas-crunchbang:~$ xrandr --output VGA1 --mode 1600x900_60.00  _60.00
```

It provides me with the proper resolution, however, it appears to be shifted a few mm to the left. By that, I mean the display itself is shifted. If I screenshot it, it comes up fine, but I see a 3 mm black bar on the right side of my screen, and I can't see the first 3 mm of the left side of my screen. If I set the resolution to the default of 1024x768 (the laptop's resolution), it appears to be fine on the external monitor. To that end, can anyone provide me with the proper command in xrandr to simply slide the display over a tad? I looked at scale and pan and neither of those appear to do what I want them to do. Also, if there is a way to set the resolution script to run at boot, I would appreciate it, as it is not currently persistent through shutdowns or reboots. Thank you very, very much.

EDIT: When I logged out and back in, I used gtf instead of cvt, and it worked a little better, in that it's shifted a bit more to center, but it still isn't exactly where it should  be.

---

### Post by ajgreeny on 2014-01-07
How is it attached, VGA cable, DVI or HDMI?

I had to adjust my monitor display to rid it of a left bias when on VGA but as soon as I got a DVI cable everything was centered properly, and in fact I can no longer adjust it even if I wanted to; no changes are available to ber made any more.

PS while on VGA I noticed that reducing the refresh rate from 75 to 60Hz also put the display back to centre.  Worth a try?

---

