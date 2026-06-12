---
title: "Upgraded from 8.04 to 8.10 with xorg issues"
date: 2009-04-16
forum: Apple Hardware Users
---

### Post by blubaustin on 2009-04-16
I Upgraded from 8.04 to 8.10 with xorg issues. The screen will go black for a bit then tell me my settings or not configured right when it was the same xorg.conf I used in 8.04.2 so.... is there something I'm missing here, that was changed in 8.10 from 8.04.2 or is just me? I have a Imac G3 600mhz, 640mb RAM, 40gb HD.

---

### Post by stream303 on 2009-04-18
As Xorg gets "smarter" for everyone else, it actually is getting tougher for us ppc'ers. :)  No longer can we rely on just moving our old xorg.conf over.

I hate to say it but with so many changes happening in xorg itself, I'd recommend updating to Jaunty 9.04 (either rc, or just wait a few days for the actual release) and try it again.  This way the pain you'll go through will at least be applicable to the latest version. :)

Or perhaps stick to 8.04.x with updates and backports etc.

Post your old /etc/X11/xorg.conf here as a base we can work from and perhaps some other users can suggest modifications that are running >8.04 at this time.

For example, here's my xorg.conf on my G5 running Debian Testing - obviously it won't work directly on your machine, but it does show how abbreviated things are these days:

```

# Section "ServerLayout"
#       Option "AutoAddDevices" "off"
# EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        BusID           "PCI:240:16:0"
        Option          "FPDither"  "true"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
EndSection

```

Much of what you have can be deleted entirely, yet others such as drivers may have to be modified.  Let's see what you are currently using.

---

