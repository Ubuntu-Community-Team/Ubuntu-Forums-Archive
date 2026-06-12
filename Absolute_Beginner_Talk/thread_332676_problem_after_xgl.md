---
title: "problem after xgl"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by Loki57701 on 2007-01-06
Ubuntu 6.10
Nvidia Geforce 7600 Go 256mb
(everything worked fine before attempted XGL/Compiz install)


-------------------------------------------------------------------
I wanted to see what all hype was about with XGL/compiz , so i followed the guide at: [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Xgl.2FCompiz_.28Nvidia.29]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Xgl.2FCompiz_.28Nvidia.29")
and upon restart of course my x server had crashed.
-----------------------------------------------------------------------
I tried:

sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10

But I got an error. Couldnt find the package or something.

then I tried:

sudo dpkg-reconfigure xserver-xorg

And it worked (sort of). When I was finished configuring the (xserver-xorg) I rebooted and I seen the Nvidia splash screen but my resolution was all messed up. In my xorg.conf file I only had up to 1024x768. And "glxinfo | grep direct" showed rendering disabled. So I removed my nvidia-glx driver and all nvidia-settings. Then removed xgl/compiz through apt.  Then reinstalled the Nvidia drivers following the guide at: [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29")
And rebooted. But my screen resolution was still messed up and redering was still not enabled. I tried changing "nvidia" to "nv" in the xorg.conf file but it didnt change anything.

I also tried adding in the resolutions to the xorg.conf file but it just crashed the xserver again (figured it would).
------------------------------------------------------------------------------------------------------
I dont want to do it but I might just reinstall. Any help getting my nvidia drivers to work again would be appreciated.

---

### Post by Sasa_Ivanovic on 2007-01-06
try this :
```

dpkg-reconfigure -phigh xserver-xorg

```

---

### Post by Sasa_Ivanovic on 2007-01-06
I'm always telling people not to install Compiz | Beryl, but they don't listen...
It's not worth the trouble!

---

