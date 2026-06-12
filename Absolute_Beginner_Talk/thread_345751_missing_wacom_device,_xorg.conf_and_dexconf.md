---
title: "missing wacom device, xorg.conf and dexconf"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by evan magers on 2007-01-24
Kubuntu Edgy. I have a recurring error in /var/log/Xorg.0.log about a missing "wacom" device. This has been addressed in [http://ubuntuforums.org/showthread.php?p=1264009](http://ubuntuforums.org/showthread.php?p=1264009) and other posts going back in time. Way back in time--google it.

Everyone posting about this error has been told to comment out the lines referring to wacom devices (touchscreen, stylus, eraser for a tablet pc) in /etc/x11/xorg.conf.

However, xorg.conf is generated automatically by /usr/bin/dexconf, and manual changes prevent further automatic updates. It's my understanding that xorg.conf should NOT be edited directly.

The device problem seems to be in the dexconf script, where the wacom devices are **hardcoded** in, with comments to fix the script to limit this device to tablet pc's only.

Is there a fixed version of the dexconf script available?

thanks

---

### Post by linear on 2007-01-24
> **evan magers said:**
> It's my understanding that xorg.conf should NOT be edited directly.

Really? If so, it's one of the most frequently broken rules. The forums are littered with video fixes that involve tweaking xorg.conf.

---

### Post by jbayone on 2007-01-24
Yeah, I'm not sure that almost every guide dealing with display or video drivers would have you edit xorg if it were that dangerous.

---

