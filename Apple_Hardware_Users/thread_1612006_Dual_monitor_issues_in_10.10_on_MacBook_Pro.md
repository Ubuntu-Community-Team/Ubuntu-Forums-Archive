---
title: "Dual monitor issues in 10.10 on MacBook Pro"
date: 2010-11-02
forum: Apple Hardware Users
---

### Post by PuckstopperGA on 2010-11-02
Hi,

I've googled and searched the forums, but either I'm not phrasing it right or I'm experiencing an odd issue. Perhaps someone's seen something like it.

I recently loaded 10.10 on my MBP. I like to use an external monitor at my desk, and have the laptop next to the monitor. I was briefly able to see 2 distinct desktops (different backgrounds, compiz themes, couldn't drag windows from screen to screen but could move mouse b/w them), which was fine, but then something screwed up. No idea what caused it to break. Now my laptop's main screen is all black. Sometimes it loads a desktop, but freezes (can't click anything) and the clock in the taskbar freezes as well. Of course it's just that screen that freezes, the external display works like a champ.

Ideally I'd like it to behave similar to OSX in that when I unplug the external display, all the open windows on the external screen return to the laptop screen. When I plug in the external display, it turns on as I would expect, without having to reload X or use Nvidia to change Xorg (it's awfully inconvenient to have to open a utility and write a new version of xorg and reboot just to enable a second display - something that other OS's like Windows and OSX seem to handle gracefully).

Any chance someone out there has any tips? Even if it's just a link or nudge in the right direction, I'd really appreciate it.

Thanks!

---

### Post by lael on 2010-11-02
I had that issue the first time I tried to setup dual monitors.  After rebooting, I tried again and it worked. I don't know if this was what did it for me or not, but I took my time and made sure I set the "make this my primary display" on the right display in the nvidia settings manager.

Probably worth filing a bug though.

---

