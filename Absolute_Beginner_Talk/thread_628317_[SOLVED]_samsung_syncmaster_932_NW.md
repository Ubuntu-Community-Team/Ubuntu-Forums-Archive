---
title: "[SOLVED] samsung syncmaster 932 NW"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by lgastmans on 2007-12-01
I just got a Samsung Syncmaster 932 NW and although the resolution was showing properly (1440 x 900), the display is not taking up the whole width of the monitor - there are two black bands on both sides. Then I went to "sceens and graphics" and saw that my previous non-widescreen monitor was still listed.

Now here is the problem: the model i bought is not listed under the Samsung monitor list. How to add it?

---

### Post by subs on 2007-12-01
press ctrl+alt+f2.... 

then login to ur account in textmode.....

then reconfigure xserver by saying ....

 > sudo dpkg-reconfigure xserver-xorg

then restart xserver saying

 > xstart

---

### Post by lgastmans on 2007-12-02
after reconfiguring with the command above this is what my xorg.conf file looks like:
Section "Monitor"
        Identifier      "SyncMaster"
        Vendorname      "Generic LCD Display"
        Modelname       "LCD Panel 1440x900"
        Horizsync       31.5-56.0
        Vertrefresh     56.0 - 65.0
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
        Gamma   1.0
EndSection

but i still don't have the monitor's full width - there are still two black bands on either side.

and "xstart" did not work, unknown command? I had to reboot my computer.

Any suggestions?

---

### Post by moonkey on 2007-12-14
I'm having the same exact problem with this monitor using gutsy. My video card is:
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02)

xrandr tells me that the resolution is correct and is the same information the monitor gives in its menu. Also it's the standard resolution of this monitor.

Screen 0: minimum 320 x 200, current 1440 x 900, maximum 1440 x 1440
VGA connected 1440x900+0+0 (normal left inverted right) 428mm x 255mm
   1440x900       59.9*+   75.0     59.9  

All seems to be configured properly. Maybe i need a special modeline for this monitor?

Any help is appreciated. Thanks.
German

---

### Post by moonkey on 2008-04-04
Well, it seems the problem is no longer here with the new Hardy Heron Beta. These are some outputs from my term.

~$ uname -a
Linux water 2.6.24-14-generic #1 SMP Thu Apr 3 04:49:29 UTC 2008 i686 GNU/Linux

~$ apt-cache policy xserver-xorg-video-intel
xserver-xorg-video-intel:
 Instalados: 2:2.2.1-1ubuntu6

~$ xrandr
Screen 0: minimum 320 x 200, current 1440 x 900, maximum 1440 x 1440
VGA connected 1440x900+0+0 (normal left inverted right x axis y axis) 428mm x 255mm
  1440x900       59.9*+   75.0     59.9

---

### Post by lgastmans on 2008-04-04
yes, just upgraded to Hardy Heron yesterday, and I am very happy to see my widescreen monitor use the full width finally...

\\:D/

---

