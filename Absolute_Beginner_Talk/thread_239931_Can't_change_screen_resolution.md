---
title: "Can't change screen resolution"
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by Eykonic on 2006-08-20
I have just installed 6.06.1 with Matrox graphics card. Preferences -> Screen resolution is stuck at 640 x 480 at 60Mhz - the drop down box is inoperable. I guess I will have to change resolution from a terminal - how?

---

### Post by Fass on 2006-08-20
```
sudo dpkg-reconfigure xserver-xorg
```

You can pick what resolutions you want to be available towards the end of that, then restart X by hitting "ctrl+alt+backspace." If it doesn't pick up the highest one (or the one you want) at once, you should then be able to use the Gnome applet to set it.

Edit: It may be prudent to save a backup of your /etc/X11/xorg.conf file before you do this, just in case.

---

### Post by slimdog360 on 2006-08-20
yikes 60MHz, thats fast. and mine only refreshes at 60Hz.

---

### Post by Fass on 2006-08-20
> **slimdog360 said:**
> yikes 60MHz, thats fast.

Heh, I didn't notice that.

---

### Post by Eykonic on 2006-08-20
My mistake. 60Hz not 60Mhz!

---

### Post by Eykonic on 2006-08-20
Thanks. That worked fine. Could not auto-detect my monitor.

---

