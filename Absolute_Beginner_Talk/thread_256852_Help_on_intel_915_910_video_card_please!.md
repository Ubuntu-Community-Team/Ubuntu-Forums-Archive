---
title: "Help on intel 915 910 video card please!"
date: 2006-09-13
forum: Absolute Beginner Talk
---

### Post by Alex.X.Zhang on 2006-09-13
Hi all,

I got this Dell Optiplex 210L at work and I installed Ubuntu on it. The text display is horrible. Text has no edge at all. everything is fuzzy. 

here is my lspci output:
0000:00:00.0 Host bridge: Intel Corporation 915G/P/GV/GL/PL/910GL Processor to I/O Controller (rev 04)
0000:00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Express Chipset Family Graphics Controller (rev 04)
0000:00:1b.0 0403: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
0000:00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
0000:00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
0000:00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
0000:00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
0000:00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
0000:00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
0000:00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d4)
0000:00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 04)
0000:00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
0000:00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 04)
0000:00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
0000:03:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller (rev 04)


Here is my xorg.conf:
Section "Device"
  identifier "Intel Corporation 82915G/GV/910GL Express Chipset Family Graphics Controller"
  boardname "Intel 915"
  busid "PCI:0:2:0"
  driver "i810"
  screen 0
  vendorname "Intel"
EndSection

Section "Monitor"
  identifier "LCD1711"
  vendorname "Generic"
  modelname "1280x1024 @ 76 Hz"
  HorizSync 31.5-82
  VertRefresh 50-90
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "640x480@85" 36.0 640 696 752 832 480 481 484 509 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync interlace +vsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1152x768@54" 64.995 1152 1178 1314 1472 768 771 777 806 +hsync +vsync
  modeline  "1280x854" 80.0 1280 1309 1460 1636 854 857 864 896 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1400x1050@75" 155.85 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  gamma 0.97
EndSection

Section "Screen"
  Identifier "Default Screen"
  Device "Intel Corporation 82915G/GV/910GL Express Chipset Family Graphics Controller"
  Monitor "LCD1711"
  DefaultDepth 24
  SubSection "Display"
    depth 24
    modes "1280x1024@60" "1280x960@75" "1280x960@60" "1400x1050@60" "1280x1024@75" "1400x1050@75" "1280x854" "1600x1200@65" "1152x768@54" "1600x1200@60" "1152x864@75" "1024x768@43" "1024x768@60" "1024x768@70" "1024x768@75" "1024x768@85" "832x624@75" "800x600@60" "800x600@85" "800x600@75" "800x600@72" "800x600@56" "640x480@85" "640x480@75" "640x480@72" "640x480@60"
  EndSubSection
EndSection

Anybody has any ideas? :confused: 

Thank you in advance.

---

### Post by coffeecat on 2006-09-13
In my experience the Intel 915G chipset with the Linux i810 driver gives a fairly good text display. Two suggestions:

Go to System > Preferences > Font. A window opens and you have four choices for Font Rendering with 'Best Shapes' as the default. Try each of the four choices. One might suit you. Most people recommend Subpixel smoothing for LCD screens, but I prefer the default.

Second suggestion is not to everyone's taste, but I like it very much. Open a terminal and type:

```
sudo dpkg-reconfigure fontconfig
``` 
You will be prompted for your password and after this there is a dialogue with three questions. The first is for autohinting. Answer yes for autohinting and then the default for the other two. Restart the X-server to see the difference (Ctrl-backspace). If you like it, all well and good. If not, just run sudo dpkg-reconfigure fontconfig again and switch off autohinting. If you are feeling adventurous you could try the other choices, but do keep a record of what the defaults were in case you want to revert back.

Some people like to simulate Windows font-rendering. Personally I think that looks like the output from a cheap and nasty dot-matrix printer, but each to their own. :? If that is what you want, suggest you search the forums. I have seen threads on this.

**Edit:** Another suggestion. It's possible that your LCD screen has not 'tuned' itself to the output from your graphics card as it is configured with that particular xorg.conf. Try pressing the 'auto' button. There should be one.

---

