---
title: "Problem with video mode"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by nuno19 on 2007-01-28
I've tried to boot from a livecd, but when I start ubuntu after loading my screen become black and nothing more happen, so I install ubuntu from an alternatecd, but now I choose ubuntu in the grub menu, it loads, and then a messange appears with this:

"Cannot display this video mode, change computer display input to 1024x768@60Hz"

Then the screen became black and nothing more.

Any ideas?

Thanks, and sorry about the english.

Edit:
I've a ati radeon 9600
AMD athlon 64

---

### Post by mikerduffy on 2007-01-28
Can you boot into recovery mode?  If so, look at /etc/X11/xorg.conf and see what screen resolutions are listed there.

---

### Post by nuno19 on 2007-01-29
I boot into recovery mode then I write "sudo nano /etc/X11/xorg.conf"

There are several depths, "4,8,15,16,24" in each one are several modes "1024x768", "832x624", "800x600", "720x400", "640x4$"

---

### Post by nuno19 on 2007-01-29
anyone? maybe a way to change resolution during the load time

---

