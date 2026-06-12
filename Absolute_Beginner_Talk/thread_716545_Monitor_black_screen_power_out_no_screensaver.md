---
title: "Monitor black screen power out no screensaver"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by hogwartsnigel on 2008-03-06
Hi forgive for cross posting, but my last one hijacked someone elses so I thought I do a stand alone query.

Me AMD3200 K8 board Nvidia fx5700 256mb Graphics card dual monitor Mitsubishi DP2070sb and Dell 1905fP 4HDD and 2 USB back up drives
I have a problem of the monitors powering down despite power management being set for never turn off.
I found a solution posted below on another thread which works but causes me to lose my dual monitor set up. The screensaver activates and that single monitor works great but the dell just is a blank screen from logon screen. I am sure its a simple solution.

This is the solution I tried that worked but disabled the dual monitors I added this to my etc/x11/xorg file, by deleting this I get both monitors back as before but they still power down.

[COLOR="Blue"]"# To prevent Blank Screen from popping up every 10 minutes
# when xgl is run as a session on display :1,
# when all the power management settings
# you normally find only concerns display :0
Section "ServerFlags"
Option "blank time" "0"
Option "standby time" "0"
Option "suspend time" "0"
Option "off time" "0"
EndSection "[/COLOR]
Thanks for any help on this niggling problem



__________________

---

