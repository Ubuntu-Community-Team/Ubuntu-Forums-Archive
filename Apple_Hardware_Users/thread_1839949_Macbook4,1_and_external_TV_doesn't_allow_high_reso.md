---
title: "Macbook4,1 and external TV doesn't allow high resolutions"
date: 2011-09-06
forum: Apple Hardware Users
---

### Post by rtega on 2011-09-06
A few months ago I suddenly couldn't use the external tv's full resolution anymore. I don't recall which revision caused this problem. I can only get to 1024x768 with xrandr.
The output from xrandr is as follows:
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 8192 x 8192
LVDS1 connected 1280x800+0+0 (normal left inverted right x axis y axis) 286mm x 179mm
   1280x800       59.9*+
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 connected (normal left inverted right x axis y axis)
   1024x768       60.0  
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  
DVI1 unknown connection (normal left inverted right x axis y axis)
   1360x768       59.8  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
TV1 disconnected (normal left inverted right x axis y axis)

The only output to my TV that is working is VGA1. The DVI1 output doesn't seem to do anything at all. I cann set it but it doesn't show anything on my tv-screen. I used to have the higher resolutions listed under VGA1 but now they are no longer available. Does anybody have an idea what's wrong here?

---

### Post by rtega on 2011-09-07
Ok, solved it myself after some googling. Here's the solution: add a new mode which supports the resolution of my screen. Your mileage may vary:

xrandr --newmode "1360x768_60.00" 84.75 1360 1432 1568 1776 768 771 781 798 -hsync +vsync
xrandr --addmode VGA1 "1360x768_60.00"
xrandr --output VGA1 --primary --mode "1360x768_60.00

---

