---
title: "Configuration for MG-17X - screen resolution fix"
date: 2006-11-18
forum: Absolute Beginner Talk
---

### Post by edgy_neil on 2006-11-18
So, I had some problems with screen resolution using my X2gen MG-17X monitor, and it took me a while to figure this out.  I was stuck with 640x480 or 800x600 as my only options, and most of the posts I came across didn't help me with this particular problem.  

Here is how you fix it:

open a terminal, and edit your xorg.conf file:
[COLOR="Blue"]sudo gedit /etc/X11/xorg.conf[/COLOR]

Scroll down until you see the "Monitor" section. It'll probably say something like:

[COLOR="Blue"]Section "Monitor"
[INDENT]Identifier    "MG-17X"
Option        "DPMS"[/INDENT]
EndSection[/COLOR]

That's not enough - apparently you need to specify your hardware a little better.

Insert these lines between the 'Option' line, and the 'EndSection' line:
[COLOR="Blue"]HorizSync 31.5-80
VertRefresh 56.3-75[/COLOR]

Once those lines are in place, you should be able to run any resolution listed in the "Screen" section (should be right below the "Monitor" section).

If you don't have this exact monitor, you need to find the appropriate settings for these numbers -- if you get it wrong, the monitor will flip out.

---

### Post by LLRNR on 2006-11-18
Right, it's **VERY IMPORTANT** to know what your specific HorizSync and VertRefesh values are. You can find this out by

```
sudo ddcprobe | grep monitorrange
```

The output will be something like *monitorrange: ab-cd, ef-gh*. The first pair of numeric values is the HorizSync and the second pair is the VertRefresh.

---

