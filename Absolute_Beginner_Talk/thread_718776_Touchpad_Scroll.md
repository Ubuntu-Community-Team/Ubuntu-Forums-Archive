---
title: "Touchpad Scroll"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by mikeypc2006 on 2008-03-08
My laptop touchpad seems to have developed a vertical scroll on the right side.  It's quite irritating as if I move my finger too far to the right, if I'm on the desktop, the desktop display will change or if I have a web browser or something open, the page will scroll.  How do I turn this feature off?

---

### Post by Arthur Archnix on 2008-03-08
Depending upon how you turned it on, there are a number of ways to turn it off. The first thing I'd do is go to your menu, >system >preferences >mouse then the "touchpad" tab, then uncheck vertical scrolling.

---

### Post by mikeypc2006 on 2008-03-08
> **Arthur Archnix said:**
> Depending upon how you turned it on, there are a number of ways to turn it off. The first thing I'd do is go to your menu, >system >preferences >mouse then the "touchpad" tab, then uncheck vertical scrolling.

I didn't turn it on.  It just seemed to happen when I installed Xubuntu.  There isn't anything like it in Windows XP.  The menu option doesn't seem to be there in Xubuntu.

---

### Post by mc4man on 2008-03-08
the default for touchpads is to have scrolling - you can turn it off by installing qsynaptics or ksynaptics
you may have to add a line to your xorg.conf
```

Option “SHMConfig” “on”
```
in the Section “InputDevice”
Identifier “Synaptics Touchpad”
 do a google search on configuring synaptic touchpad in ubuntu for info first

---

### Post by Arthur Archnix on 2008-03-08
Try adding this to your xorg.conf
```
 Option "VertEdgeScroll" "false"
```
It would go under your synaptic section. So, 
gksudo mousepad /etc/X11/xorg.conf
looks for this:
> 
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizEdgeScroll"       "0"
        Option          "SHMConfig"             "true"
EndSection
if you don't see it, then add it. And add the below SHMConfig. You'll need to restart 'x' by logging out or hitting ctrl+alt+delete

---

