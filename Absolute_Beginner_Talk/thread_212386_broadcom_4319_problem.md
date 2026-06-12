---
title: "broadcom 4319 problem"
date: 2006-07-09
forum: Absolute Beginner Talk
---

### Post by stevieb on 2006-07-09
Hello,


I have a Lenovo 3000 C100 (Linux only- no Windows) and cannot get the wifi card to show up in the Network Settings window.  I have tried several of the HowTo guides in this forum, but none have worked.  My card is a Broadcom 4319; I have tried both drivers for the 4318 series- bcmwl5.inf, and bcmwl5a.inf.  I have copied the files to my desktop along with the .sys file (and no one seems to know what to do with this file- does it just sit in the same directory while the inf file is installed, or should this also be installed?) and this is what happens:

[CODE]
sudo ndiswrapper -l
No drivers installed

sudo ndiswrapper -i bcmwl5a.inf
Installing bcmwl5a
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2

sudo ndiswrapper -m
modprobe config already contains alias directive

sudo ndiswrapper -l
Installed ndis drivers:
bcmwl5a         driver present

[ENDCODE]

At this point my wireless card is not listed in the Network Settings dialog. I should also mention (and this is probably where I need to start) that in Device Manager, the card is listed as "Unknown (0x4319)."  I appreciate any help; sorry if this has been discussed before, but I've been plowing through the forums for 2 days now and have yet to find a solution.

-steve

---

