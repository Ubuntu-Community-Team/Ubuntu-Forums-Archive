---
title: "Changing Monitor Refresh Rate"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by fjf314 on 2007-02-24
I'm having a minor issue with changing the refresh rate on my system.  Ubuntu runs my monitor at 75 Hz.  According to my monitor's specs, though, it is optimized for 60 Hz, so that is what I would like to run it at.  If I open the Screen Resolution utility, I can select 60 Hz from there without any problems.  My refresh rate will change from 75 to 60, and everything is good until I reboot my system, at which point the refresh rate reverts back to 75.  How do I go about making this change permanent?

I ran some searches around the forum, but most of what I found seemed to deal with people wanting refresh rates that *weren't* available in the Screen Resolution utility and trying to make those available.  The rate I desire is available, I just want to make it permanent so I don't have to change it every time I turn my system off and on again.
 
I would post my xorg.config file, but I am unfortunately not at my own machine right now, I'm at work.  If that's needed, I'll try to post it as soon as I get the chance.

Thanks for any help!

---

### Post by annda on 2007-02-24
back up your xorg.conf and then change max refresh rate from 75 to 60 (in the file). that should be enough.

---

