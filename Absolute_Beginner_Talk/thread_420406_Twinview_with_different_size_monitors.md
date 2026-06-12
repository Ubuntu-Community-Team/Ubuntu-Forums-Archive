---
title: "Twinview with different size monitors?"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by funkychicken9000 on 2007-04-23
Bit of a beginner here really.  I just installed Feisty and after a bit of mucking around got the nvidia drivers loaded with twinview support.  Here's the problem though: my two monitors are completely different (1920x1200 and 1280x1024) and with twinview the smaller of my monitors shows only a section of the complete desktop.  It misses off either the bottom or the top, or both depending on the exact positioning I set in the twinview gui.  Is there any way round this?  In windows my smaller monitor effectively shrinks the desktop and so you still get the full picture, surely there must be equivalent behavior in ubuntu?

---

### Post by annda on 2007-04-23
use this:
sudo nvidia-settings

or create a launcher with this line as the command:
gksudo nvidia-settings

make sure to configure both displays as separate screens, not twinview. that way, you will be able to use different resolutions.

save to xorg.conf before exiting and restarting X. (back up xorg.conf first!)

---

