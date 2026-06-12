---
title: "Trying to change display resolution"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by FloridaGeezer on 2007-02-15
I have a display monitor that supports 1920x1200.  I dual-boot kubuntu (Dapper Drake) and Windows XP.  Windows is able to display the 1920x1200, but kubuntu is only allowing choices up to 1024x768.  I thought maybe I needed to download new drivers for the video card (NVIDIA) since the kubuntu is using a VESA driver.  NVIDIA has drivers, but the proceedures for installing them includes a need to recompile a kernal interface.  It appears that to do this I need a linker program called ld.so and that should be in /usr/bin/ but I cannot find the linker there (or anywhere else).  Am I completely on the wrong track here?  Also, if I try  System Settings, the Display resolution is capped at 1024x768 - so I tried Administrator Mode - it asked for my password which I entered, and it fails saying it can't communicate with root.  Do I have to bypass sudo and enable root as the ubuntu online manual suggests to not do?

Wes

---

### Post by Toet on 2007-02-15
You can add the drivers by select nvidia-glx in Synaptic. This should install the drivers.

Then you should adjust the X-window config file to use them.

This can be done by the following command in a terminal-window:

```
sudo nvidia-glx-config enable
```

Restart X, and you should be fine to select more.

Getting higher resolutions the possible to choose from at that moment is possible by adjusting the X-configuration file by hand.

---

### Post by punx45 on 2007-02-15
if you are still having trouble, you can try the [envy script]("http://albertomilone.com/nvidia_scripts1.html").   It was the only way i could get my nvidia drivers working properly.   

... and after all that work my monitor died and now that system runs headless.. sigh.

---

### Post by FloridaGeezer on 2007-02-15
Toet and punx45,

Thanks to you both.  With your help I've made some progress and now have got the display to accept some changes.  I'm still confused about not being able to find the linker, but at this point I'm past the main issue.

Wes

---

