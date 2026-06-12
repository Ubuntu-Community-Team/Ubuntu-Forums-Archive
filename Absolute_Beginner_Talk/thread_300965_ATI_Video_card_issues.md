---
title: "ATI Video card issues"
date: 2006-11-16
forum: Absolute Beginner Talk
---

### Post by andrew222 on 2006-11-16
I was getting a staticy picture on my CRT monitor, so I switched to a LCD monitor, and that did not put an end to it.  So I uninstalled the driver for my ATI Readon 9800 xt and downloaded the latest proprietary driver from the ATI web site.  And that did not put an end to it.  However, when I go to my Windows XP partition there is no static.  Can any of the Linux experts out there tell me what I can do to get rid of this before having to buy a new video card??

Andrew

---

### Post by wpshooter on 2006-11-16
Try this.

Go to Synaptic and search for "fglrx".  And install driver and then restart machine.

Then use sudo gedit to edit your "/etc/X11/xorg.conf" file,  find the video cards section for your 9800 xt and the replace the parameter that says "ati" with "fglrx".  Save file.
Then restart machine.

---

### Post by andrew222 on 2006-11-16
Thank you wpshooter,

I'll try it out and see how that works.

Andrew

---

