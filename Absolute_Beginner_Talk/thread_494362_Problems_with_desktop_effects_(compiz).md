---
title: "Problems with desktop effects (compiz)"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by ferpadro on 2007-07-06
Hi everyone! I succeeded to buy a GeForce 7100 GS and installed ubuntu. First thing i did was enabling desktop effects. When i executed the command the system popped up a message telling me that the graphic card was not installed and that it needed to download several restricted drivers (i checked with glxinfo | grep direct and i didnt have direct rendering enabled). I downloaded them, restarted the machine and enabled desktop effects again. I opened System menu and i noticed the effects, the screen were smooth when scrolling and had that uber effect when moving. But i opened firefox and noticed that the bar where the name of the program is displayed was not being shown. In every application i open i notice the lack of this bar. I cannot maximize, minimize, move or close the windows i open. Any ideas on how to resolve this?

Best regards

---

### Post by starcraft.man on 2007-07-06
Ok, bear with me I hope I get this right. I'm mostly a Beryl user... I've seen this problem numerous times though on nvidia machines, and my suspicion was only more confirmed by [ubuntu geek.]("http://www.ubuntugeek.com/compiz-and-nvidia-on-ubuntu-feisty-fawn.html")

Its just a simple line to the xorg.

1) Open any terminal please.

2) Paste in and enter:

```
gksudo gedit /etc/X11/xorg.conf
```

This will of course open up xorg.conf file with gedit.

3) Now scroll down your xorg till you find this entry (yours will be different), add what is in red. Make sure it lines up with above, i.e. option under bus and such, I like it looking neat :).

```
Section "Device"
        Identifier      "nVidia Corporation NV40 [GeForce 6800 GT]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
[COLOR="Red"]        Option          "AddARGBGLXVisuals"         "True"[/COLOR]
EndSection
```

That should do it I believe. I think its the exact same error as Beryl users get.

---

### Post by ferpadro on 2007-07-06
thanks a lot ill try it and answer you inmediately

---

