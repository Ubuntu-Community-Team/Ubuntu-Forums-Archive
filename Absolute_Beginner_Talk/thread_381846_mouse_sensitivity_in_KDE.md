---
title: "mouse sensitivity in KDE"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by qrm on 2007-03-11
Hi!

I have used Ubuntu for over a year now but only used Gnome. Now I installed KDE and I cant find the place to change the sensitivity to below 1.0x. Im using Razer diamondback and the cursor movement is awfully quick. Any help is much appreciated.

---

### Post by astrolabio on 2007-03-11
press Alt+F2

Insert in the run command window 
     kcontrol


Then go in Peripherals/Mouse and then to the  Advanced Tab

That's it

EASIER WAY;
Click on the K-menu (the K button in the taskbar)
Sytem Settings
in the third row click on  
Keyboard And Mouse 
Go to the advanced tab

that's it

---

### Post by qrm on 2007-03-11
I already found that place, just that the lowest senitivity offered there is 1.0x for pointer acceleration and this is **way** too high

---

### Post by vinchi007 on 2007-03-11
what file contains info, per user profile in linux, sensitivity of the mouse.
I have 2 computers -> switch -> 1monitor/1keyboard/1mouse.
Linux box after switch install and hookup, my mouse if moving too fast.

Which file contains sensitivity of the mouse? (no gui app please, I have xterm not installed linux locally)

---

### Post by qrm on 2007-03-11
I am going to try lowering my mouse resolution in xorg.conf from 1600 to something lower.

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ExplorerPS/2"
Option "Buttons" "7"
Option "Resolution" "1600"
Option "ZAxisMapping" "4 5"
Option "ButtonMapping" "1 2 3 6 7"
Option "Emulate3Buttons" "true"
EndSection

---

