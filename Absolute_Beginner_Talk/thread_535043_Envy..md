---
title: "Envy."
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by Liamkerrigan on 2007-08-26
Hello everyone, i  downloaded envy yesterday got it installed and working perfectly the problem I am having is that i set me screen resolution using envy, im running a NVIDIA Geforce 8800GTS, to 1680x1050 and works (sometimes) then i restarted my computer and go up to the ubuntu log-in screen and it seemed to still be the same 1680x1050 resolution, but once i actually got onto the computer it went back to the ugly 1024x768. Please help me this is annoying. Thanks in advance.

Monitor - Dell 20"
Graphics Card - Ge force 8800GTS 640mb

---

### Post by wolfen69 on 2007-08-26
in terminal:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by r4ik on 2007-08-26
Try  sudo gedit /etc/X11/xorg.conf   in a terminal and make it look like this use you're own res. (replace 1600x1200 by 1680x1050)

Section "Screen"
Identifier "Default Screen"
Device "Nvidia 8800 GTS"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1600x1200" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1600x1200" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1600x1200" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1600x1200" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1600x1200" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1600x1200" "1024x768" "800x600" "640x480"
EndSubSection
EndSection

Save the file and you should be fine.

Good luck !

---

