---
title: "ATI driver issues"
date: 2006-09-29
forum: Absolute Beginner Talk
---

### Post by lounsbud on 2006-09-29
I have just re-installed Ubuntu on an old Compaq Proliant 800 server. It is a Pentium II machine with integrated video. The problem I am having is after installation (which works well as far as I can tell) the only resolution I have available is 640x400. Which in itself would not be an issue but most of the windows are cut off to the point where I can't click OK or see options that happen to fall in that area. I have tried updating the ATI driver using a procedure found at [www.cchtml.com](www.cchtml.com) to no avail. I did notice that my card is not listed in the supported HW section.

My HW is as follows:
ATI 3D Rage IIC 215IIC [Mach 64 GT IIC] - as listed in device manager
Dell P991 monitor - as autodected in dpkg-reconfigure xserver-xorg

Any help would be greatly appreciated! Thanks in advance!

---

### Post by petri on 2006-09-29
Have you tried with "vesa" when you did the dpkg-reconfigure xserver-xorg ?

---

### Post by geezerone on 2006-09-29
Have you tried [COLOR="Purple"]**dpkg-reconfigure xserver-xorg**[/COLOR] to add extra resolutions? I haven't tried it with ATI drivers though.

---

### Post by bodhi.zazen on 2006-09-29
[[color=blue]Leading and Bleeding with XFree86 4.0 and KDE 2 Beta[/color]](http://linuxplanet.com/linuxplanet/previews/1833/3/)

> Alas, though xf86config ran perfectly and even had my card on the list, it ended by telling me that my adapter was unsupported and would only run as generic VGA. That being, er, less than optimum for a Web development workstation, I did some empirical hacking around at the XF86Config file, and eventually ended up with one that worked. The relevant sections of the file for the ATI Xpert98 look like this:

Section "Device"
    Identifier  "ATI Mach64 GT (264GT), aka 3D RAGE"
    Driver      "ati"
    VideoRam    8192
EndSection

 Identifier  "Screen 1"
    Device      "ATI Mach64 GT (264GT), aka 3D RAGE"
    Monitor     "Sony 210GS"
    DefaultDepth 24
    Subsection "Display"
        Depth       24
        Modes       "1280x1024"
        ViewPort    0 0
    EndSubsection
EndSection

Of course, your system's configuration will be different unless you have the same hardware as me. 

---

### Post by lounsbud on 2006-09-29
Thanks for the feedback...

> Have you tried with "vesa" when you did the dpkg-reconfigure xserver-xorg ?
No I hadn't. When I did I still only have 1 option for resolution but at least it is 640x480 instead of 640x400. Its movement in the right direction anyway...

> Have you tried dpkg-reconfigure xserver-xorg to add extra resolutions? I haven't tried it with ATI drivers though.

I have tried this and it had no effect.

Thanks again but any other ideas? The thing that gets me is that it is such and old card. I figured I would have no problems with drivers...shows what I know!

What should I try next?

---

### Post by petri on 2006-09-29
[www.google.com/linux](www.google.com/linux) and there you should find something.


btw when you did "sudo dpkg-reconfigure xserver-xorg" did you choose better resolution with your spacebar? You could also try with "sudo dpkg-reconfigure -phigh xserver-xorg"






EDIT: [http://www.linux-drivers.org/](http://www.linux-drivers.org/)

---

### Post by web-keeper on 2007-02-26
see this thread I posted it might help...!

[http://ubuntuforums.org/showthread.php?p=2214167#post2214167](http://ubuntuforums.org/showthread.php?p=2214167#post2214167)

Goodluck
Jon (web-keeper)

---

