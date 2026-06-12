---
title: "Resoulution is 640 x 400:(!"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by LollYouSuckZor on 2007-05-12
Alright I have had this happen before.   How do I get it back to 1024 x 768?

Video Card: Nvidia Geforce FX ( Generic )
Driver; Nvidia

It was at 1024 x 768 until I changed the driver to the Nvidia driver, now it's at something like 640 x 400 :(


=[ [http://img204.imageshack.us/img204/456/snapshot3wz8.png](http://img204.imageshack.us/img204/456/snapshot3wz8.png)

---

### Post by taurus on 2007-05-12
Did you install an nVidia driver before you change the Driver in /etc/X11/xorg.conf from "nv" to "nvidia"?

```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by hammedhaaret on 2007-05-12
have you tryed in the system/settings/screen resolution menu?

if that doesn't work. try to press ALT+F2 and write "nvidia-settings" to open a nvidia settings menu.    then under the 'X server Display Configuration' you should be able to change the configuration to the desired res

hope that it'll help you out
hammedhaaret

---

### Post by LollYouSuckZor on 2007-05-12
Sorry guys :( I apologize. 

I got it working, I went through some huge thing I saw in an old forum, it wasn't working before because my sources.list was really really corrupt.  It's working now :) Thanks :D

---

