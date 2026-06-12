---
title: "Monitor starts flickering after some time (only in linux)"
date: 2013-10-09
forum: Any Other OS
---

### Post by JMmB7A4 on 2013-10-09
Dear All,

i am using Linux Mint 15 (which is based on 13.04 Ubuntu) and after some time, maybe 10-20 minutes, my TFT starts flickering. This also occured with the original release of Ubuntu 12.04.
My monitor is a Cornea CT1701 (TFT), which is connected to the DVI connector with a VGA Cable and an adapter. 
My first guess was that it had to do with the Hz setup and resolution, because Ubuntu 12.04 would always switch to 72 Hz, but now it is set to 60hz and it still has the same issue.

When i start Linux, it takes some time for the effect to show and then it is getting stronger over time.
Flickering is maybe not the right word. You can see horizontal stripes (similar to a TV-Screen) moving from top to bottom or sometimes the other way around. You can see them the best when displaying big gray areas on the screen. It's not really disturbing, but I fear for the Screen, that it gets damaged over time.

I've been using Windows 7 in Dual Boot before, and the effect didn't show there. Only if I switched to Windows from Linux it would stay for some time.

Here is what my monitor OSD shows (which is the same as in windows):
[TABLE="class: outer_border, width: 500"]
[TR]
[TD]1280x1024
64 Khz
60 Hz[/TD]
[/TR]
[/TABLE]

Output of xrandr is:
[TABLE="class: outer_border, width: 500"]
[TR]
[TD]Screen 0: minimum 8 x 8, current 1280 x 1024, maximum 8192 x 8192
DVI-I-0 disconnected (normal left inverted right x axis y axis)
DVI-I-1 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 360mm x 290mm
   1280x1024      60.0*+   75.0     60.0  
   1920x1080      59.9  
   1680x1050      59.9  
   1440x900       59.9  
   1400x1050      60.0  
   1360x768       60.0     59.8  
   1280x960       60.0  
   1152x864       75.0     75.0     70.0     60.0  
   1024x768       75.0     70.1     60.0  
   960x600       120.0  
   960x540       120.0  
   840x525       139.8    120.0    119.8  
   832x624        74.6  
   800x600        75.0     72.2     60.3     56.2  
   720x450       119.8  
   700x525       120.0  
   680x384       119.9    119.6  
   640x480        75.0     72.8     59.9  
   512x384       140.1    120.0  
   400x300       144.4  
   320x240       145.6    120.1  
TV-0 disconnected (normal left inverted right x axis y axis)
DVI-I-2 disconnected (normal left inverted right x axis y axis)
DVI-I-3 disconnected (normal left inverted right x axis y axis)[/TD]
[/TR]
[/TABLE]
Sorry for the long post, instead of pasting random logs and similar now I better wait for comments, cause I don't know what is important.
I tried a lot of things like using a custom EDID but nothing worked. I haven't found anything helpful on the net so far.

Did anyone discover similar with other screens?
I'd be really happy for helpful answers! Thanks in Advance!

---

### Post by howefield on 2013-10-09
Thread moved to the "*Other OS/Distro Support*" forum.

---

