---
title: "eMac G4 internal monitor adjustment"
date: 2011-03-20
forum: Apple Hardware Users
---

### Post by teachop on 2011-03-20
With an install of 10.10 on an eMac G4 1.25, the screen works "out of the box" in a lot of different resolutions.

However, there is no way to adjust the horizontal, and the screen is off to the left, clipping a few pixels.  Is there a way to fix the horizontal position?  There is no xorg.conf and I am thinking there must be a new way?

Ubuntu is working quite well on this machine and this is just a small tweak I would like to take care of.

---

### Post by linuxopjemac on 2011-03-20
can you give me a link of your machine in everymac.com pls ?

---

### Post by teachop on 2011-03-20
> **linuxopjemac said:**
> can you give me a link of your machine in everymac.com pls ?
This looks like the right one:
[http://www.everymac.com/systems/apple/emac/stats/emac_1.25.html]("http://www.everymac.com/systems/apple/emac/stats/emac_1.25.html")

---

### Post by Ms. Daisy on 2011-10-18
> **teachop said:**
> This looks like the right one:
[http://www.everymac.com/systems/apple/emac/stats/emac_1.25.html](http://www.everymac.com/systems/apple/emac/stats/emac_1.25.html)
Same machine, same question here.  Did you find an answer?

---

### Post by rsavage on 2011-10-19
Hi Ms Daisy,
 
Can you try adding modelines to an xorg.conf file as described in the long lubuntu thread [http://ubuntuforums.org/showpost.php?p=11020435&postcount=1](http://ubuntuforums.org/showpost.php?p=11020435&postcount=1)?  I think you should come out with something like this:
 
```

Section "ServerLayout" 
Identifier     "X.org Configured" 
Screen         "Screen0" 
EndSection   
 
Section "Monitor" 
Identifier   "Monitor0" 
VendorName   "Monitor Vendor" 
ModelName    "Monitor Model" 
ModeLine "1024x768" 100 1024 1108 1280 1408 768 768 780 796 +hsync +vsync 
ModeLine "1152x864" 100 1152 1173 1269 1440 768 769 772 800 +hsync +vsync 
Modeline "1280x960"  124.54  1280 1368 1504 1728  960 961 964 1001  +HSync +Vsync
EndSection   
 
Section "Device" 
Identifier  "Card0" 
Driver      "nouveau" 
BusID       "PCI:0:16:0" 
EndSection   
 
Section "Screen" 
Identifier "Screen0" 
Device     "Card0" 
Monitor    "Monitor0"  
 
DefaultDepth 16  
 
SubSection "Display" 
Viewport   0 0 
Depth     1
EndSubSection 
 
SubSection "Display" 
Viewport   0 0 
Depth     4 
EndSubSection 
 
SubSection "Display" 
Viewport   0 0 
Depth     8 
EndSubSection 
 
SubSection "Display" 
Viewport   0 0 
Depth     15 
EndSubSection 
 
SubSection "Display" 
Viewport   0 0 
Depth     16 
EndSubSection 
 
SubSection "Display" 
Viewport   0 0 
Depth     24 
EndSubSection 
EndSection 

```From what I gather nvidia cards have the choice of the nouveau driver (the newest) or the nv driver. I've added a DefaultDepth line to the above. You can try it with and without.

---

### Post by Ms. Daisy on 2011-10-20
> **rsavage said:**
> Hi Ms Daisy,Can you try adding modelines to an xorg.conf file as described in the long lubuntu thread?  Don't boot into single user mode, just try the commands from a normal terminal.Hi rsavage. I was hoping I just wasn't able to find a window in the GUI that would do this. I swear I saw a thread a while ago about adjusting an Apple screen but I can't find it again (note to self- if it looks useful, subscribe or lose it forever!)  Oh well.  I will probably upgrade after I've finished reading a manual or two. If the monitor adjustment is still a problem I'll give this a try in 11.10. Thanks.

---

### Post by ant2ne on 2011-12-23
I've got the same issue with my emac g3. I reset the pram by powering off the emac. then holding the p r option and command keys until I heard 4 bongs. This DID center the screen better. not perfect, but much better.

---

