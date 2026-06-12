---
title: "MacBook5,1 and Twinview"
date: 2009-10-11
forum: Apple Hardware Users
---

### Post by bas1 on 2009-10-11
I've been struggling to get Twinview working properly on my MacBook5,1. In Ubuntu 9.10 beta 1 can enable Twinview with an external display but not without a massive amount of screen 'problems' (hard to describe, see the images attached) on the external display. This doesn't happen in OS X.

Any suggestions?

---

### Post by Niels den Otter on 2009-10-12
Ouch. Out-of-sync.

Is your display sending EDID information and have you not configured your X-server/Nvidia driver to igore this? EDID information allows the monitor to indicate the horiz sync and vert refresh information and the supported resolutions.

You could look for 'edid' in your /var/log/Xorg.0.log (grep -i edid /var/log/Xorg.0.log) and read the lines close to these to understand if EDID information is send and used.


-- Niels

---

### Post by bas1 on 2009-10-15
I'm pretty sure you're right. However, the Xorg log file (attached) makes no mention of anything with regards to EDID except for when it gets the DPI. In nvidia-settings, I can get a dump of the EDID from the external monitor. 

The resolution is correct, but the vertical/horizontal sync is still way off. Anything else I can do?

---

### Post by proycon on 2009-10-16
I'm currently experiencing the exact same problem on a MacBook5,3 with karmic,

---

### Post by proycon on 2009-10-17
I posted about this issue on the [nvidia forum]("http://www.nvnews.net/vbulletin/showthread.php?p=2106289#post2106289"). It doesn't work well yet, but I managed to get it to work somewhat with the newer 190.40 drivers, but running on a lower resolution. At least that's better than the out-of-sync thing.

---

### Post by linuxnovice on 2009-11-26
Hi,

I am having the same problem with Macbook5,1 running Jaunty. Any improvment on this issue?
Thanks.

---

### Post by proycon on 2009-11-26
This issue should now be fixed with the NVIDIA 195.22 beta drivers. Get them from [http://www.nvnews.net/vbulletin/showthread.php?t=122606](http://www.nvnews.net/vbulletin/showthread.php?t=122606) . 

I tried today and my monitor works again!

---

### Post by buntuLo on 2009-11-26
thanks for the update, i'll try it soon!

---

### Post by linuxnovice on 2009-11-27
Thanks!

It works perfectly.

---

