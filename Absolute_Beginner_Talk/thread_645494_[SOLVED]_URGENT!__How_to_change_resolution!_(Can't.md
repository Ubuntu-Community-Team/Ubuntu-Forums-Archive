---
title: "[SOLVED] URGENT!  How to change resolution! (Can't see)"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by Kosimo on 2007-12-20
I did change my monitor in (Screen and graphics)  

Now... I can't see anything...       There is any way to change back?? 

Recovery mode doesn't works either.. 


Is this information saved on x.org?   Can I edit this from command line?

Plzzzz!!  

Help!!!!!     :(:(:(:(:(

---

### Post by shadow-of-sin on 2007-12-20
If you can access the command line, you should be able to change your resolution by editing the xorg.conf file:
```
sudo nano /etc/X11/xorg.conf
```

There should be a section like this: (ofcourse yours will be slightly different)
```
Section "Screen"
    Identifier    "Default Screen"
    Device        "NVIDIA Corporation NV34 [GeForce FX 5200]"
    Monitor        "CM752ET"
    DefaultDepth    16
    SubSection "Display":
        Depth        16
        Modes      "1280x1024" "1024x768"
    EndSubSection
EndSection
```

Just change the "Modes" section and you should be able to go back to your previous resolution.

---

### Post by Kosimo on 2007-12-20
> **shadow-of-sin said:**
> If you can access the command line, you should be able to change your resolution by editing the xorg.conf file:
```
sudo nano /etc/X11/xorg.conf
```

There should be a section like this: (ofcourse yours will be slightly different)
```
Section "Screen"
    Identifier    "Default Screen"
    Device        "NVIDIA Corporation NV34 [GeForce FX 5200]"
    Monitor        "CM752ET"
    DefaultDepth    16
    SubSection "Display":
        Depth        16
        Modes      "1280x1024" "1024x768"
    EndSubSection
EndSection
```

Just change the "Modes" section and you should be able to go back to your previous resolution.



Solved:

Thanks a lot ;)

---

