---
title: "Ubuntu doesn't recognize screen and graphics card"
date: 2008-06-18
forum: Apple Hardware Users
---

### Post by sixsidepentagon on 2008-06-18
So I was just doing an update of the system, and I accidentally restarted the computer before it was done. When I got back into it, it told me that it couldn't recognise the monitor or graphics card, and gave me some choices for it. First I just went with the plug and play default, which sort of worked except it was low resolution. So I chose one thing for the monitor based on an educated guess, and I'm pretty sure I screwed up. The first time I went back in, it just gave me the same low resolution screen, but then when I turned it on again later, the screen was split into 6ths, and had random bars everywhere. It was hard even to navigate it to shut down. So is there any way to force it to give me the recognition menu again, or make it just recognize the hardware again (including the graphics card)?

---

### Post by sixsidepentagon on 2008-06-18
Oh, it's a Macbook 4.1, by the way.

---

### Post by cyberdork33 on 2008-06-19
start Ubuntu in Recovery Mode (An option in the Grub Menu), then when you get to a terminal, run:
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` then reboot, and you should hopefully get a somewhat working screen. If you get that far without problems we can try to diagnose other issues, but who knows what might have been broken in the interrupted update.

---

### Post by sixsidepentagon on 2008-06-19
Haha, I actually went into recovery mode, and I just reset xorg and redetected hardware, and now it all works (though the touchpad needs to be reset now, no biggie). Thanks mate!

---

### Post by cyberdork33 on 2008-06-19
> **sixsidepentagon said:**
> Haha, I actually went into recovery mode, and I just reset xorg and redetected hardware, and now it all works (though the touchpad needs to be reset now, no biggie). Thanks mate!
bascially the same thing the command I posted does.
Please mark as solved if it is now fixed.

---

