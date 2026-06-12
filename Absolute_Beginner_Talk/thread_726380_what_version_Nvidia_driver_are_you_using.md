---
title: "what version Nvidia driver are you using?"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by garyed on 2008-03-16
I'm running FX5200 & everytime I try to install the Driver from Nvidia's site I can't get back into my desktop. I have to copy my saved xorg.conf to get back again.
Just curious what version/chipset/distro  you Nvidia guys are using that works.
I've tried the newest driver running gusty & ubuntu studio. Tried with both kernels & still no go.

---

### Post by dokdoom on 2008-03-16
After you install the driver have you checked your xorg.conf to make sure it's listing the proper driver? You would think it would do that for you automatically but I would defiantley take a look.

---

### Post by bumanie on 2008-03-16
The latest driver will not work with that graphics card, it is now quite an old card. You will get on better with this driver NVIDIA-Linux-x86-96.43.05-pkg1.run form here [http://www.nvidia.com/object/linux_display_x86_96.43.05.html](http://www.nvidia.com/object/linux_display_x86_96.43.05.html)

---

### Post by louieb on 2008-03-16
The restricted driver (**nvidia**) and the **nv** driver both will work with that card.  I have that card in 2 computers. 
Heres what I have in /etc/X11/xorg.conf

 ```

Section "Device"
    Identifier    "nVidia Corporation NV34 [GeForce FX 5200]"
    Driver        "nvidia"
    Busid        "PCI:1:0:0"
    Option        "AddARGBVisuals"    "True"
    Option        "AddARGBGLXVisuals"    "True"
    Option        "NoLogo"    "True"
EndSection

```Whenever x fails to start for me 99% of the time its because somehow my horizontal and vertical refresh rate is set to high.  If you have your monitors manual check to see what the maximum refresh rate is. If you can't find it try setiing the maximum below 60 for an lcd or 75 for a crt.
may have to play a little with it.
```

Section "Monitor"
    Identifier    "Generic Monitor"
    Option        "DPMS"
    [COLOR=Blue][B]Horizsync    28-64
    Vertrefresh    43-60[/B][/COLOR]
EndSection

```

---

### Post by garyed on 2008-03-16
Thanks for all the replies,
I finally found the problem & it ended up being my KVM switch which I forgot to mention.
I ended up using the "System>Administration>Restricted  Drivers Manager" to get things working. The main monitor is on a KVM switch on my Gusty computer which is the one that I also use a second monitor with. With the default installation Gusty worked fine with the KVM switched monitor but when I tried to use the second monitor which is not on the KVM switch it wouldn't work. With both Edgy &  Feisty I already knew that they didn't work right with the KVM switch but when I installed Gusty it worked perfectly with the KVM switch I didn't thnk it would cause a problem. Once I tried installing Nvidia drivers all hell broke loose. So now I'm back to the original xorg.conf & one monitor working fine with the KVM switch. I'm not even sure what driver I was using when both monitors were working but I made a backup of the xorg.conf file I used & it did have in it the lines mentioned:

Section "Device"
    Identifier    "nVidia Corporation NV34 [GeForce FX 5200]"
    Driver        "nvidia"
    Busid        "PCI:1:0:0"
    Option        "AddARGBVisuals"    "True"
    Option        "AddARGBGLXVisuals"    "True"
    Option        "NoLogo"    "True"

Now if I can only find a KVM switch that works right with Linux I'll be in business.
I've already got two & they both have the same problems but they work fine in Windows

Thanks again to all ,

---

