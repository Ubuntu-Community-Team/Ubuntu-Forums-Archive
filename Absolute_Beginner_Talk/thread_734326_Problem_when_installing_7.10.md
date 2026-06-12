---
title: "Problem when installing 7.10"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by munch3 on 2008-03-24
When I try to boot this message is displayed;
Cannot display this video mode, change computer display input to 1024x768@60Hz

---

### Post by Patb on 2008-03-24
Munch. 

Try a restart in Recovery mode.  Then back up your existing xorg.conf eg:
```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak1
```

Then run:
```
dpkg-reconfigure xserver-xorg
```

If in doubt, choose the defaults. This should bring you back to the default video settings.

Then reboot with ctrl-alt-delete.  

If that doesn't work, restart in Recovery mode and edit /etc/X11/xorg.conf.  In this file, under the "screen" section, there should be the line beginning "Modes...".  In this line, delete any modes higher than "1024x768". Then save and reboot.  

Good luck, Pat

---

