---
title: "Setting default screen resolution"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by ronald_stall on 2007-03-15
I have a Nvidia 7600 GS video card and my monitor has a native screen res of 1400x900 but the computer boots up and always starts with screen res 1152x768 but when I go to System > Preferences > Screen Resolution and set it to 1400x900 it does it but when I restart the system it is back to 1152x768. I assume I can edit the /etc/X11/xorg.conf file but am not certain what to edit to make it the default everytime the system boots for all logins.

Thanks

---

### Post by taurus on 2007-03-15
Yes, you need to add that resolution to /etc/X11/xorg.conf.  Look toward the end where you see a bunch of lines with resolutions in them.  Add "1400x900" to the beginning of those lines.  Save it and reboot.

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by Aliarse on 2007-03-15
Im guessing you've already tried ticking the "Make default for this computer?" option?

If so, you could try editing xorg and removing any un-needed screen resolutions and see if that fixes the problem. On mine, doing this stops the login screen from using 1280x1024, and instead uses my default res of 1440x900.

---

