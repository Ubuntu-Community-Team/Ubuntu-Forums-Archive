---
title: "Help! I screwed up XFCE resolution somehow"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by deldredge on 2007-07-04
Ok,
I was changing the resolution in XFCE through the regular graphical program to do that, and somehow I screwed it up by refusing the new resolution, and it set it to something rediculous like 320x240 or something! the toolbars on the top and bottom of the screen take up like 50% of the real estate. 

Needless to say, I can't get anything open after I've booted into xfce to change the resolution, as it won't display on the low resolution. 

Is there something I can type into the command line before I start xfce that will change the resolution? Will it make the change so that next time when I start XFCE normally it will be at a decent resolution?

Thanks,
Dan

---

### Post by meborc on 2007-07-04
try ```
sudo dpkg-reconfigure xserver-xorg
```in the xfce resolution chooser, choose the "default" resolution link!

---

### Post by deldredge on 2007-07-04
I couldn't find anything in there that said anything about the XFCE Resolution chooser. I unchecked 640X480 in the resolution list, but it's still booting up at the really low resolution.

---

### Post by deldredge on 2007-07-04
I just restarted into xfce at the low resolution, managed to get the display manager open, and pushed tab blindly until a usable resolution came up. Problem solved. Thanks.

-Dan

---

