---
title: "Resolution for iMac G3 [tray loading] running Ubuntu 7.04 is very low [512 X 384]"
date: 2007-06-03
forum: Apple PPC Users
---

### Post by iMac233 on 2007-06-03
Resolution for iMac G3 [tray loading] running Ubuntu 7.04 is very low [512 X 384] and the option to higher resolution is not available. 

Card info as shown by OS 8:
Card Type - Display
Card Name - ATY, Rage IIC_C or llC_C
Model - ATY, GT-Bc

- How can this be fixed? 
- Would this require new display driver for iMac? If yes, where can I download these from?

---

### Post by Salpiche on 2007-06-03
open a terminal and use this command *sudo dpkg-reconfigure xserver-xorg* then follow directions, there is one option that will allow you to change the resolution, just select the highest known for your iMac.

---

### Post by iMac233 on 2007-06-06
Thanks for the suggestions, tried couple of times but this is not working :(

---

### Post by stmiller on 2007-06-06
Check out the 3D info under the PPCFAQs at the link below. It has some more help on getting graphics drivers going. All drivers for PPC Linux are there in the kernel- there are none to fetch from the internet.

---

### Post by jazzman on 2007-06-08
lines 1-3 weren't pertinent to your question and were deleted. Try steps 4 - 11

4. Press CRTL-ALT-F1. This brings up the command line.
5. Now we need to edit the Xorg.conf file. Type: sudo nano /etc/X11/xorg.conf
6. Add a "#" at the line that says LOAD DRI. This keeps it from loading.
6a. Go to area near the bottom under "Monitor" and adjust the HorizSync to 60 and VertRefresh to75-117 respectively.
7. Go to the the area (towards the bottom of the file) where the default Depth is and change it from 24 to 16.
8. Save and exit out of nano.
9. Type: sudo killall -HUP gdm
10. This will kill and restart the GUI.
11. You will get a screen resolution of 800 x 600 with 16 color depth.

---

### Post by iMac233 on 2007-06-10
Thats awesome jazzman... that worked and in fact I got 1024X768 ;)

Note: I added the line VideoMem = 102400 KB, but not sure if memory is the reason for higher resolution than 800X600, but I am sure you would be able to conclude it better:)
 

Thanks stmiller, I am going through the link and will try it soon..

Thanks all for all the help in making it possible for me to have my iMac run Ubuntu 7.0.4 as I wanted :)

Cheers...

---

### Post by WolfHeart on 2007-06-12
Hi, i have the exact same imac, however, after following this thread to fix the resolution problems i too get 1024x768, but that is even with there being absolutely no mentioning of that resolution in xorg.conf! This puzzles me alot!

The monitor for the imac is not really made for 1024x768 and therefore gets kinda blurry and does not fill the entire monitor correctly, resulting in eye and headaches. any help is much appreciated :D

---

### Post by davidd00 on 2007-06-12
[COLOR="DimGray"]I'm new with Ubuntu and with Mac. A fried has given me a iMac G3 and I wanted to setup Ubuntu on it.
My first question is quite stupid. In the Ubuntu download page I don't see any PPC version for 7.04, which one do I use? Sun UltraSPARC?
Thanks and sorry for the so newbie question[/COLOR]
Sorry for the quiestion, I think  I have already found the answer searching in the Ubuntu documentation. [PowerPCFAQ]("https://wiki.ubuntu.com/PowerPCFAQ#head-8d764a92cbe82911913d972b8189698f9f04e6f3")
Finally, I think I'm going to install Edubuntu, as I want to prepare this computer for my kids

---

