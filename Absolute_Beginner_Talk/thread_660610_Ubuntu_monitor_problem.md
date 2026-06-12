---
title: "Ubuntu monitor problem"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by Joe_E on 2008-01-07
Ubuntu does not come up on monitor
I have a compaq presario 2500 laptop that has a broken screen. It works fine when a acer AL1716W monitor is plugged into the back.

I booted from the Live CD fine. Could see everything and went through the complete install. I took the CD out and then rebooted. The screen first shows the BIOS screen clearly. It then shows several boxes of blue lines and then the monitor says "Input not Supported".

The GRUB does come up and I can get into the recovery mode.

Thanks in advance for any help.

---

### Post by Hospadar on 2008-01-07
probably the issue is that your system is trying to output a resolution/refresh rate/sync range that your monitor doesn't support.  You might try looking up the native resolution for your monitor, the sync range, refresh rate, etc for your monitor and reconfiguring your xserver

When you get the blue boxes, do a ctrl-alt-F1 to get a text terminal.

Then do ```
sudo dpkg-reconfigure xserver-xorg
``` and go through the dialog and pick the resolutions and sync ranges you want.  any options you don't know about you can probably just default through.

If you arn't sure, you could just start at the lowest resolutions and sync ranges and work your way up until you find something that works and looks good.

---

