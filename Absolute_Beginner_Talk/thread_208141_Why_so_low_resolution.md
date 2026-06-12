---
title: "Why so low resolution?"
date: 2006-07-03
forum: Absolute Beginner Talk
---

### Post by jincast90 on 2006-07-03
Why can I only set my desktop resolution at a maximum of 1024*768? In Windows I can set it to 1280*1024. And yes, I have a 17 inch monitor, which should be able to pull this off.

---

### Post by bikeboy on 2006-07-03
Common problem. Firstly, tell us what kind of video card you have.

---

### Post by jincast90 on 2006-07-03
I have a Radeon 9200.

---

### Post by wolfmaniac on 2006-07-03
change the resolution settings in /etc/X11/xorg.conf

---

### Post by MaximB on 2006-07-03
will it be supported if I type it manually ?

---

### Post by Jagot on 2006-07-03
Yes, but you'll need to quit the xserver and reload it for it to take effect.

---

### Post by jincast90 on 2006-07-03
When I type this, it says that my entry is denied.

---

### Post by Dazaablack on 2006-07-03
I think you have to log out. Then press CTRL + SHIFT + BACKSPACE.

I had the same problem dude. I am just gonna do it remotely via SSH and reboot the machine tomorrow when i get out of bed. :D

Will this work with a Geforce 6600GT PCI-E x16.

I have installed the dapper nVidia drivers and can run games on wine :D

- I am so impressed with Ubuntu right now

---

### Post by Dazaablack on 2006-07-03
[QUOTE=Dazaablack]I think you have to log out. Then press CTRL + SHIFT + BACKSPACE.

I had the same problem dude. I am just gonna do it remotely via SSH and reboot the machine tomorrow when i get out of bed. :D

Will this work with a Geforce 6600GT PCI-E x16.

I have installed the dapper nVidia drivers and can run games on wine :D

- I am so impressed with Ubuntu right now[/QUOTE]

Me again.. 

So do I just wap in 1280x1024 in with this lot?

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV43 [GeForce 6600 GT]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

---

### Post by wolfmaniac on 2006-07-03
yes make it your first entry and leave the rest same .
restart xserver or better reboot.
then select the desired resolution

---

