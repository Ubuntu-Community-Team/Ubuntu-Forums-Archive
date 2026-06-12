---
title: "[SOLVED] Wifi icon"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by superintelligentape on 2007-12-20
Err...okay I accidentally deleted both the wifi strength indicator and battery life icons on the top right icon cluster. I got the battery icon back from the add to panel menu (under the title notification area) but I cant find the wifi ico.

---

### Post by wormser on 2007-12-20
I just copied this from a post I did before,  It sounds like you can ignore the Notification Area part.  I Just figured somebody else might need all the details when running into this thread.

> I have done this before and think this is one thing that needs to become more user friendly. You need to add Notification Area. If they still are not appearing then go to System> Preferences> Sessions. Look for Network Manager and Power Management. Make sure they are checked. If they are not there then click add and use the following information.

Name: Network Manager
Command: nm-applet --sm-disable
Comment: Network Manager applet

Name: Power Manager
Command: gnome-power-manager
Comment: Power management daemon

---

### Post by superintelligentape on 2007-12-20
The Icon for the  network manager is checked and the code is the same as what you posted...it says its running under the current sessions tab

---

### Post by wormser on 2007-12-20
What happens when you run the command in a shell?

```
nm-applet --sm-disable
```

---

### Post by superintelligentape on 2007-12-20
You mean in terminal? This comes out:

/home/vikash/.themes/LiNsta3/gtk-2.0/menubar-custom.rc:22: Unable to locate image file in pixmap_path: "Menu-Menubar/menubar-black.svg"
/home/vikash/.themes/LiNsta3/gtk-2.0/menubar-custom.rc:25: Background image options specified without filename
/home/vikash/.themes/LiNsta3/gtk-2.0/menubar-custom.rc:31: Unable to locate image file in pixmap_path: "Menu-Menubar/menubar-black.svg"
/home/vikash/.themes/LiNsta3/gtk-2.0/menubar-custom.rc:34: Background image options specified without filename

---

### Post by RomeReactor on 2007-12-20
Hi. It looks like a problem with your current theme; try switching to Human or Clearlooks, and if the icon is still not there, press ALT+F2 and run **nm-applet --sm-disable** again.

---

### Post by superintelligentape on 2007-12-20
Oops...All I had to do was restart :lolflag:

---

### Post by wormser on 2007-12-20
I am glad it worked.  Now mark your thread resolved.

---

