---
title: "1920 x 1200 resolution"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by brz3rk on 2007-04-17
Hello.  I have a monitor that supports 1920 x 1200 but I can't seem get beyond 1600 x 1200 and the screen is stretched.  How can I get it upto 1920 x 1200?  Also, I don't think I have the drivers for the video card but I'm not too sure.  Is there a way to check?

I have the following:

- NVIDIA GeForce FX 5200 video card
- fresh install of ubuntu 6.10 with all the updates


Any help would be greatly appreciated

---

### Post by Jagot on 2007-04-17
Run this command:

```
glxinfo | grep rendering
```

If it says yes then you have installed the drivers for your video card, if no then you have not.

---

### Post by brz3rk on 2007-04-17
It looks like I dont' have the drivers installed and will need to search for the way to do so on these forums.  Any ideas about the resolution issue or would that be related to the video card drivers?

---

### Post by MyR on 2007-04-17
this may or may not work, i have a different grafics card but i was able to get the proper ratio at least.
run "sudo dpkg-reconfigure xserver-xorg" making sure to select 1920x1200 and 1680x1050 (the proper ratio) then reboot.

---

### Post by mand0 on 2007-04-17
> **brz3rk said:**
> It looks like I dont' have the drivers installed and will need to search for the way to do so on these forums.  Any ideas about the resolution issue or would that be related to the video card drivers?

Follow the instructions [here]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Beta_Graphics_Driver_.28NVIDIA.29") to get your nvidia drivers working.

---

### Post by kpkeerthi on 2007-04-17
If you want the latest nvidia driver, try this [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by brz3rk on 2007-04-17
Thanks for the support everyone.  The [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Beta_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Beta_Graphics_Driver_.28NVIDIA.29) worked! :D  1920x1200 goodness!



.. now, onto beryl

---

