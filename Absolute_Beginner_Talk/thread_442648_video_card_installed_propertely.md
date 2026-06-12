---
title: "video card installed propertely?"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by krisfrajer on 2007-05-13
Hi folks
How do I know my video card + drivers are installed correctly? I have an ati radeon 9600TX on an AMD64. When I try to enable desktop effects, it does not work (system cannot enable it) plus the acceleration driver when activated gives me black screen and removes ubuntu graphical interface completey ... ie when I restart my baby I just get this black screen. I have the feeling my card is not installed correctly. Thus:

1) is there any way to know I have the proper driver set up?
2) How can I set up my proper driver for this card?

This is what I get in my xorg.cong file @ /etc/X11
Something I want to remark is that I have a dual monitor system. i am not into configuring this system yet. I want to figure out my card system first. i just installed ubuntu and working my way around to install the right drivers for my hardware (Yeah I also need to configure my soundblaster X-fi).

Thxs,


Section "Device"
Identifier "ATI Technologies Inc RV350 AR [Radeon 9600]"
Driver "ati"
BusID "PCI:1:0:0"
EndSection

Section "Monitor"
Identifier "F9AH(ANA)"
Option "DPMS"
EndSection

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies Inc RV350 AR [Radeon 9600]"
Monitor "F9AH(ANA)"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1280x1024" "1024x768" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1280x1024" "1024x768" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1280x1024" "1024x768" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1280x1024" "1024x768" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1280x1024" "1024x768" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1280x1024" "1024x768" "800x600" "720x400" "640x480"
EndSubSection
EndSection

---

### Post by overdrank on 2007-05-13
> **krisfrajer said:**
> Hi folks
How do I know my video card + drivers are installed correctly? I have an ati radeon 9600TX on an AMD64. When I try to enable desktop effects, it does not work (system cannot enable it) plus the acceleration driver when activated gives me black screen and removes ubuntu graphical interface completey ... ie when I restart my baby I just get this black screen. I have the feeling my card is not installed correctly. Thus:

1) is there any way to know I have the proper driver set up?
2) How can I set up my proper driver for this card?

This is what I get in my xorg.cong file @ /etc/X11
Something I want to remark is that I have a dual monitor system. i am not into configuring this system yet. I want to figure out my card system first. i just installed ubuntu and working my way around to install the right drivers for my hardware (Yeah I also need to configure my soundblaster X-fi).

Thxs,


Section "Device"
Identifier "ATI Technologies Inc RV350 AR [Radeon 9600]"
Driver "ati"
BusID "PCI:1:0:0"
EndSection

Section "Monitor"
Identifier "F9AH(ANA)"
Option "DPMS"
EndSection

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies Inc RV350 AR [Radeon 9600]"
Monitor "F9AH(ANA)"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1280x1024" "1024x768" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1280x1024" "1024x768" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1280x1024" "1024x768" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1280x1024" "1024x768" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1280x1024" "1024x768" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1280x1024" "1024x768" "800x600" "720x400" "640x480"
EndSubSection
EndSection

Hi I assume you have read and tried the sticky in forum
[http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)
Good luck hope that helps! :guitar:

---

### Post by krisfrajer on 2007-05-13
Hi I try everything in the link but did not work. I get a nice black screen and nothing else. I will try to install the drivers directly from the ati supplier. It has some funny steps... 

[http://ati.de/support/drivers/linux64/linux64-radeon.html](http://ati.de/support/drivers/linux64/linux64-radeon.html)

How do I know is correctly install?

---

### Post by Hobo Joe on 2007-05-13
type 'glxinfo' in the terminal and scroll to the top where it says 'direct rendering', if it says yes, then you are clear, if not.... well, then you need to try again.

---

