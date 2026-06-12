---
title: "Trouble loading X on Mac Pro with Nvidia Gfx"
date: 2009-02-04
forum: Apple Hardware Users
---

### Post by bernie9998 on 2009-02-04
I'm trying to install Intrepid Ibex onto my Mac pro model 1,1 with an Nvidia Geforce 7300 GT graphics card.

I had previously had this machine dual booting between OSX and gentoo and it had been working fine, however I had wanted to switch to Kubuntu instead.

Upon starting the livecd, I found X would fail to bring the graphic console up properly-- instead I would receive a random color on the screen.

Switching to a text console and checking dmesg shows this odd message:
```

type mismatch for 80000000, 10000000 old: write-back new:write-combining

```

I believe this is related to the X display issue as it repeats when I attempt to restart the X server (/etc/init.d/kdm restart):
```

no mtrr for 80000000, 10000000 found
type mismatch for 80000000, 10000000 old: write-back new:write-combining

```

Has anyone else encountered this issue?  Thanks in advance for any assistance.

---

### Post by bernie9998 on 2009-02-09
I was able to work around this issue.  Apparently, the open source video drivers will not work with this system (due to the issues stated in previous post).  I'm not sure if the Xorg server loads up the nv module or the more generic vga module, so I'm not sure where this bug lies, however I was able to get my graphics console working fine with the proprietary nvidia graphics driver.

Here's the steps I did to get this to work (first on the livecd, then again after the install process was completed):

1. Install the nvidia driver module
```

sudo apt-get install nvidia-glx-177

```

2. Add basic Xorg config file (/etc/X11/xorg.conf) to get the server to load the proprietary driver:
> 
Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver  "nvidia"
        Option  "NoLogo"        "True"
EndSection

(This config file was taken from another (K)ubuntu system which had generated it automatically from the Hardware Drivers application.)

3. Reload the X server:
```

sudo /etc/init.d/kdm restart

```

---

