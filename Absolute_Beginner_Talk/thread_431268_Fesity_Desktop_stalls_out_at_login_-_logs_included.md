---
title: "Fesity Desktop stalls out at login - logs included"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by willz06jw on 2007-05-02
Howdy Team,

My Feisty desktop computer sometimes stalls out at the first login screen.  I can't seem to figure out why, but I have a copy of the Xorg.0.log.old to see if one of you genuies can help.

Here is what it says at the end of the file:
```
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : Success
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : Success
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : Success
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
```


Thanks again for looking or helping,
Will from Texas

---

### Post by louieb on 2007-05-03
At least you get to the logon screen. I was having trouble getting there. 
MY fix was to boot to the older 2.6.20-14 kernel. Then use Synaptic to reinstall the  2.6.20-15 kernel. After a while my problem popped back up. This time I did the same thing plus I removed the **quiet splash **from the kernel line in menu.lst.
Haven't had a problem since.

---

### Post by willz06jw on 2007-05-05
I bet that would work, but I am not happy unless everything is working well -- and taking away the soft splash screen would kill me.

Anyway it only happens ever so often, so I will live with it for now.  I have had hardware problems with my current video card, so I believe that may be the issue.

Will

---

