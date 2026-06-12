---
title: "Video Problems"
date: 2005-06-12
forum: Apple PPC Users
---

### Post by Gex on 2005-06-12
Well Im a newbie to linux just installed it about 2 hours, everything seems fine but the video on my PB 15" 1.25.  For some reason I have some flickering lines on the right half of the screen.  You can barely notice them, but it is some what annoying since I have no problems when I boot into OSX.

---

### Post by elvis on 2005-06-24
On LCD displays, flickering lines can often mean incorrect refresh rates being sent to your screen, which results in "flickering" or "tearing" as your one half of your screen shows different information to another half of your screen.

If OSX is working fine, then I would assume your graphics card does not have any physical faults, and the problem is most likely a software setting such as refresh rate.

Edit your /etc/X11/xorg.conf file to change your maximum refresh rate.  Mine looks like:

```

Section "Monitor"
   Identifier                   "monitor0"
   HorizSync                    30 - 120
   VertRefresh                  60 - 85
   Option                       "dpms"
   Gamma                        1.6
EndSection

```

Notice the "VertRefresh" has valid modes 60 - 85Hz.  For an LCD, I would use "50 - 60" instead.  If yours is set upwards of 75Hz, it might be the problem.

Do not change other values like your HorizSync unless you know what you are doing.  This can cause damage to your monitor if set incorrectly.

---

### Post by Gex on 2005-06-28
Thanks for the help.

---

