---
title: "Intel 945GM/PM/GMS, macbook, and second display 1680x1050"
date: 2007-10-19
forum: Apple Intel Users
---

### Post by coulix on 2007-10-19
Hello,
I have a mac book running ubuntu with no problems (after tweaking for keyboard and wifi). Today i tried to plug my desktop screen samsung 226BW 1680x1050:

When i plug it; it gets detected and i get a clone mode (laptop screen / desktop screen) working in 1280x800

xrandr gives me:
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 1680 x 1680
VGA disconnected (normal left inverted right)
LVDS connected (normal left inverted right)
   1280x800       59.9 +   60.0  
   1280x768       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
TMDS-1 connected 1280x800+0+0 (normal left inverted right) 0mm x 0mm
   1680x1050      59.9 +   60.0  
   1280x1024      75.0     59.9  
   1280x960       59.9  
   1280x800       60.0* 
   1152x864       75.0     74.8  
   1280x768       60.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     66.7     60.0     59.9  
   720x400        70.1  


so that seems all good.

However a **xrandr -s 1280x1024 **or **xrandr --screen 0 1680x1050** makes the samsung screen change his resolution but some kind of image flickering/warping disturbance arise.

Strange it looks different from refresh rate error:
[IMG]http://coulix.net/temp/screen_bug.JPG[/IMG]

---

### Post by coulix on 2007-10-19
maybe i should post in video card cat ?

---

### Post by david_edmundson on 2007-10-19
I get this if I have my VGA monitor attached when X starts before xrandr commands are run.

Are you still leaving your in built screen running?

Also try changing the resolution with: This sets the monitor to use a resolution rather than the virtual screen size.
xrandr --output TMDS-1 --mode 1680x1050

or even 
xrandr --output TMDS-1 --auto

---

### Post by coulix on 2007-10-20
its working thanks !!!

---

