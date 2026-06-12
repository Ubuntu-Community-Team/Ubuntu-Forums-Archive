---
title: "New installation..."
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by John Hill-Tout on 2006-10-04
Greetings to all.
I am a relative newcomer to Linux and Ubuntu but I'm impressed. I have a PC with a Sempron 3300+ and 1024 Mb of RAM.
Here is my problem; when installed, Ubuntu 6.06 defaults to a resolution of 1600x1200, which my older model eyes finds a bit tiny. When I change the resolution of 1280x1024 I get bounced back to the login screen and I'm back to 1600x1200.
Has anyone else run into this problem or have any suggestions?

---

### Post by theratster on 2006-10-04
The hacking way to fix it is by going to the xorg.conf file (it is located in /etc/X11 I believe and then find the spot where it shows all of the different resolutions (its like "1600x1200" "1200x768" etc. and then delete the ones infront of the resolution you want. The first resolution listed is the default one. So by deleting the ones you don't want, you make the one you want default.

---

### Post by Marsolin on 2006-10-04
I'm using Kubuntu so I'm not sure of the exact tool if you are using Gnome. I've found that instead of just changing the resolution I have to go change the settings for the monitor so it lists the resolution I want to run as its max. In KDE both can be done through Display in the System Settings. I assume that Gnome is similar.

---

### Post by jhaitas on 2006-10-04
marsolin
what theratster refers to is at a lower level than KDE or Gnome... /etc/X11/xorg.conf is the configuration file for the X server... KDE and Gnome run on top of the X server... if you remove references to 1600x1200 from your /etc/X11/xorg.conf file, KDE and Gnome won't even know it is possible to run at that resolution...

remember... you must be root to do this...

---

### Post by Marsolin on 2006-10-04
> **jhaitas said:**
> marsolin
what theratster refers to is at a lower level than KDE or Gnome... /etc/X11/xorg.conf is the configuration file for the X server... KDE and Gnome run on top of the X server... if you remove references to 1600x1200 from your /etc/X11/xorg.conf file, KDE and Gnome won't even know it is possible to run at that resolution...

remember... you must be root to do this...

That was exactly my point. Changing the monitor's capabilities through the GUI will automatically remove the resolution from xorg.conf.

---

### Post by podunk on 2006-10-04
Before you change it back it up! :-)

```
 sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_back_up 
```

---

### Post by jhaitas on 2006-10-05
changing the gui settings will have no effect upon /etc/X11/xorg.conf...
/etc/X11/xorg.conf lists all available resolutions...
changing the gui settings simply selects one of these available resolutions...

---

### Post by petri on 2006-10-05
Resolution problems depends on **no videodrivers**. Write **lspci** in terminal/konsole and you will see which graphicschips you have. Make a **Search** up at the title bar: **howto install ***** where *** is your graphicscard

P.S. No need to hack the *.conf-files, why not just **sudo dpkg-reconfigure xserver-xorg**. But first the drivers!

---

