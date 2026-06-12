---
title: "Screen Resolution and mouse configuration"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by pallukucchu on 2007-03-06
I recently installed  Ubuntu 6.10, the newest Ubuntu release on my notebook pc.
I have following two issues which I want to resolve:

1.Screen Resolution:
 Step1:
 I click the system icon and click the system resolution on the drop down menu. I get a window saying screen resolution preferences.
It contains

Default settings 
Resolution  1024X 768
Refresh rate 60Hz
Rotation   normal/left/inverted/right

There is no other option in the resolution menu(unlike windows).

Step2:
I went to the terminal screen and typed
sudo gedit /etc/X11/xorg.conf

I changed the settings as follows
....
......

Default depth 24
.....
.....
.....

Subsection  "Display"  
   Depth    24
  Modes  "1680X1050" " 1280X800" "1024X768" " 800X600"
EndSubSection

EndSection
..........
.........

This didnt resolve the desktop screen resolution.
I request input from the experienced users.

2. I have a USB optical mouse with scroll wheel. 
  The cursor moves on its own. 

I went to the same file

sudo gedit /etc/X11/xorg.conf

 and changed  

Section "Input Device"
  Identifier  "Configure Mouse"
  Driver     "mouse"
  Option   "Core Pointer"
  Option   "Device"  "/dev/input/**mice**
  Option   "Protocol"  "ExplorerPS/2"
  Option   "ZAxisMapping"  "4 5"
  Option   "Emulate3Buttions"  "true"
EndSection

I replaced the mice with mouse1 and saved the file.

Even then it doesnt seem to work.
The touchpad mouse is working fine.

I request input from experienced users regarding this also.

---

### Post by magicfab on 2007-03-06
Post separately for each problem, otherwise this gets confusing and doesn't help people using the search engine having to read through unrelated issues.

For 1), try a lower color depth. 16 ?
For 2) you need to find a way to disable your touchpad when the USB mouse is in use (or permanently). Search for that. You may also have the option of doing it in your computer's BISO settings.

---

### Post by maniacmusician on 2007-03-06
1. Many possibilities here. What kind of card do you have? what driver are you using? post the device section of our xorg.conf. Also, you need to restart the X server after changing xorg.conf (ctrl + alt + Backspace)

---

### Post by NewOldTimer on 2007-03-06
If you have a synaptics touchpad  you can load "qsynaptics" from the package manager, its an app that will allow you to disable/enable the touchpad. Check your /etc/x11xorg.conf  file, should be under identifier.

---

