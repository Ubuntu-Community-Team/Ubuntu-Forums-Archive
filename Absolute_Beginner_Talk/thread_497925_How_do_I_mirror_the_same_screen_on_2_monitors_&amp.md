---
title: "How do I mirror the same screen on 2 monitors &amp; same resolution?"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by Atomic Dog on 2007-07-10
I have a laptop with Intel 945 video.  When I connect a second monitor and boot it displays on both (which is what I want), but at the maximum resolution of the external monitor.  The resolution I want is not available in the "screen resolution" options (again with the monitor connected from boot), yet the external monitor does handle it (tested).

So how to I force one resolution only for this computer whether an external monitor is plugged in or not when booting?  Is there a way to make the system only have one video resolution setting either way?

I am using the xserver-xorg-video-intel driver.  I hope I'm making sense.  I want to be able to unplug the monitor and move around as often I take my laptop with me around the building.  When I start with my desktop monitor plugged in, I can't do this as I only see a fraction of the whole screen on the laptop.  A true dual monitor setup won't work either as I don't have the desk space to have the laptop open.

---

### Post by bodhi.zazen on 2007-07-10
Open a terminal, enter :```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Scroll through the resolutions, select only the resolution you want (remove any higher resolution)

Scroll through selections with up and down arrows.

Select/Deselect with the space bar

Re-start X (log out)

---

### Post by Atomic Dog on 2007-07-10
Didn't work.  I did as you ask, and when I restarted it came up in a higher resolution, and all the resolutions up to 1680 x 1050.  Do I need to get out of gdm before running the command?  Reboot to a prompt or something?

Remember I am trying to use a resolution that the monitor does not report it can handle.

---

### Post by Atomic Dog on 2007-07-10
I figured out how to do it.  Bodhi was right about reconfiguring X11, but I also had to disable DDC.  Once DDC (a plug and play monitor module) was disabled the monitor on my desk and monitor on the laptop had the same resolution (that I forced configuring x11).

So thanks for the setup tip.  And remember kids...plug and pray can be a good thing most of the time.

in x11.conf I had to add under the monitor section:          Option          "DDC" "false"  I also remarked it out of the modules section for good measure.

---

