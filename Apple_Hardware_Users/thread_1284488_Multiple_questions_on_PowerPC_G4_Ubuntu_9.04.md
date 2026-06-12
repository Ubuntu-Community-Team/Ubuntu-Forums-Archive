---
title: "Multiple questions on PowerPC G4 Ubuntu 9.04"
date: 2009-10-06
forum: Apple Hardware Users
---

### Post by buntybuntu on 2009-10-06
HI all,
 
First of all I want to tell you that I am very new to Ubuntu/Linux, let alone Ubuntu on an Apple. I have installed, Ubuntu 9.04 (Jaunty Jackalope) on my Apple PowerBook G4 17". This computer has a 1 GHz PowerPC processor, 80 GB HDD, 1GB RAM and wireless/wired interrnet access. 
 
The installation was remarkably simple and straight forward. So far everything is working great. I have wireless internet access, sound and installed all the latest updates without any problems. Now my questions:
 
1. The video card on this computer is an Nvidia GeForce4 MX with 64 MB of video ram. Is this good enough to run Compiz? I tried enabling visual effects and I get a message saying, "Can not enable Visual effects". I ran ***glxgears*** and was able to see the animation. Also the etc\X11\xorg.conf looks like this:
 
*************************
Section "Device"
Identifier "Configured Video Device"
BusID "PCI:0:16:0"
EndSection
 
Section "Monitor"
Identifier "Configured Monitor"
EndSection
 
Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
EndSection
****************************
 
That does'nt seem right now does it? How can I install Nvidia drivers?
 
2. I ran update using update manager and all the updates were installed successfully. Yet my Firefox is at version 3.0.14, when I know for sure that version 3.5 is out there and on my windows computers. Why can't I update my firefox to 3.5. "Check for Updates" is greyed out. How can I get the latest version of firefox installed?
 
Thanks,
 
Any help would be greatly appreciated.
 
BuntyBuntu

---

