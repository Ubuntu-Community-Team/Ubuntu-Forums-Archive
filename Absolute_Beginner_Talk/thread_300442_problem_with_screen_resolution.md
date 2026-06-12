---
title: "problem with screen resolution"
date: 2006-11-15
forum: Absolute Beginner Talk
---

### Post by sebiskaa on 2006-11-15
hi,
i have a problem with my 19" LCD monitor (Viewsonic vp930b), ubuntu only displays 640*480. i don't know how change the screen resolution to 1280*1024 @60 Hz which is the preferred resolution for my monitor. viewsonic doesn't offer driver support for linux, they sent me a few files for creating my own driver. how can i change the screen resolution? is there any risc if i use the wrong settings (forcing a higher resolution)?
thanks.

---

### Post by macdo on 2006-11-15
Funnily enough, there's a thread just a few minutes old that deals with this:

Two possible solutions: 
One, in a console, run ```
sudo dpkg-reconfigure xserver-xorg
```
Two, edit xorg.conf and add your prefered resolution:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo nano /etc/X11/xorg.conf
```

In this file, add your resolution to the list in the screen section :
```

Section "Screen"
Identifier "Screen0"
Device "Videocard0"
Monitor "Monitor0"
DefaultDepth 24
SubSection "Display"
Viewport 0 0
Depth 24
Modes "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
EndSubSection
```

Obviously, only change the resolution settings...

HTH

---

### Post by sebiskaa on 2006-11-15
i checked out my xorg.conf file and my resolution already exists in the list in the screen section. is it because i am not logged on as root that i can't change the resoultion? i can't log on as root from the first session screen, but it works from a terminal. how can this be? any ideas?

---

### Post by yurtfg89327tfg0o on 2006-11-15
Whats you video card?
You may need to check xorg.conf for that.

---

### Post by sebiskaa on 2006-11-15
i have a geforcee 6600, 256 MB, 128 bit (Sparkle). it's displayed as geforce 6600 GT in  xorg.conf, section screen, device.

---

### Post by sebiskaa on 2006-11-15
i have a geforcee 6600, 256 MB, 128 bit (Sparkle). it's displayed as geforce 6600 GT in xorg.conf, section screen, device.

---

### Post by LordExcelsior on 2006-11-15
I tried the second method that macdo suggested, however, I was not successful.  I cannot change my resolution to the resolution that I have added to the xorg.conf file.

---

### Post by gentlemanmasher on 2006-11-15
have you tried system>preferences>screenresolution in the sytem menu?

---

### Post by ljpm on 2006-11-15
> **macdo said:**
> 
 in a console, run ```
sudo dpkg-reconfigure xserver-xorg
```



As macdo said. I had the same problem and reconfiguring xserver-xorg did the trick.

Something to keep in mind, your monitor may not be detected. If this occurs you will have to enter Hscan and Vscan values. Check your monitor manual or on line.

---

