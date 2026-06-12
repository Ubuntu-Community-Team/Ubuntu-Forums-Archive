---
title: "Another screen resolution issue"
date: 2011-12-12
forum: Asus Ubuntu Support (CLOSED)
---

### Post by chrislamuk on 2011-12-12
Hi guys,

I have Ubuntu 10.04 installed on my asus eee pc 1005pe netbook, as you all know these netbooks have a fairly low screen resolution 1024x600.

The problem I have regards certain menus which dont seem to fit on the screen, for example when I press Crtl-P to print something the OK and cancel button cannot be selected as they disappear below the bottom edge of the screen.

Is there a fix for this problem?

---

### Post by patricio_kevin on 2011-12-26
i have the same problem :(

---

### Post by donc786 on 2011-12-30
Me too tried lots of different things, pretty much given up on it. I just press tab and hope i'm at the right spot when I press enter.

---

### Post by marco_polo99 on 2012-01-11
Same here--I can get in Xrandr and manually create the 1024 x 600, but when I apply it the screen resizes with an offset--meaning there is about an inch of wasted black space at the top of my screen.  The resolution may be correct, but because of the shift the bottom of the screen is still missing

---

### Post by adrien214 on 2012-01-18
what does your ~/.config/monitors.xml file look like?

---

### Post by silentstone on 2012-01-19
Maybe you can fake a 1024x768 resolution to fully view those programs that seem to expect 768 minimum height; binding a script to a keyboard shortcut makes it a quick fix when programs run off-screen. This worked on my Eeepc 1005hab in Ubuntu 10.04 and 11.04...

Created script, toggle-zoom, to toggle between 1024x768 and 1024x600 resolutions:
_~/bin/toggle-zoom.sh_
> #!/bin/sh

if xrandr | head -n1 | grep -q '1024 x 600'; then
  xrandr --output LVDS1 --scale 1.0x1.28
else
  xrandr --output LVDS1 --scale 1.0x1.0
fi
Here's where I found that and some tweaks to recover more screen-space from toolbars, buttons, and the like:  [https://help.ubuntu.com/community/EeePC/Using#Customizing_the_tiny_desktop](https://help.ubuntu.com/community/EeePC/Using#Customizing_the_tiny_desktop)

---

