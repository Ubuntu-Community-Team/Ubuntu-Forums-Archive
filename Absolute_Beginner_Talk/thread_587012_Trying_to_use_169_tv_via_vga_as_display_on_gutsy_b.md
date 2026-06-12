---
title: "Trying to use 16:9 tv via vga as display on gutsy but not working.. please help!"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by dorean on 2007-10-22
Hi, i just successfully installed gutsy on my pc, but it only works on my 4:3 pc monitor.

When i plug it into my tv, however, it'll go into grub and il select ubuntu but the screen will go black and my tv just says no signal (which is what it does when theres nothing plugged in to that specific input). Im using a vga input and vista works just fine like this. 

Im using a Radeon X1600 512mb "hypermemory" (which apparantly is actually just 256) and im plugging it into a 26" LG 720p lcd tv via vga.

---

### Post by dorean on 2007-10-22
bump

---

### Post by dorean on 2007-10-23
Come on, does no one have any idea how to solve this?

---

### Post by dorean on 2007-10-23
Guess i just have to keep bumping till someone comes along...

---

### Post by stinkypudding on 2007-10-23
I had a similar issue trying to run in 720p mode when I upgraded.  But I'm using an Nvidia 6600GT.   I finally had to go back to Feisty with the older driver.   The new driver kept defaulting to "safe" mode when I tried updating my xorg config.   Anyway, I'm no expert on HDTV, but I don't believe it's possible to get HD with VGA.   I think you have to use HDMI or Component cables(I'm using YPbPr component cable).    But I can tell you it is possible, I'm in 720p now on a Go Video 27 inch HDTV.   Here's the relevant part of my Xorg config:

Section "Monitor"
# HorizSync source: xconfig, VertRefresh source: xconfig
Identifier "Monitor0"
VendorName "Unknown"
ModelName "TV-0"
HorizSync 28.0 - 150.0
VertRefresh 28.0 - 150.0
Option "DPMS"
Modeline "1280x720" 74.48 1280 1336 1472 1664 720 721 724 746 -HSync +Vsync

EndSection

Section "Device"
Identifier "Videocard0"
Driver "nvidia"
VendorName "NVIDIA Corporation"
BoardName "GeForce 6600"
Option "ConnectedMonitor" "TV"
Option "UseEDID" "False"
EndSection

Section "Screen"
Identifier "Screen0"
Device "Videocard0"
Monitor "Monitor0"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1280x720" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
Option "TVStandard" "HD720p"
Option "ConnectedMonitor" "TV"
Option "TVOutFormat" "COMPOSITE"
EndSubSection
EndSection

Section "Extensions"
Option "Component" "Enable"
Option "Composite" "Enable"
EndSection

---

