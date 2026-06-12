---
title: "Wacom Graphire 2 and cursor alignment"
date: 2007-07-09
forum: Art &amp; Design
---

### Post by Lorkki on 2007-07-09
Howdy,

I just recently got hold of the aforementioned drawing tablet model, size A6, which is an absolute dream to use with Photoshop as opposed to mousing around. So I thought I'd try it out with GIMP and Inkscape as well, after booting to my Feisty installation. I plugged it in and instantly took control of the mouse pointer, which was already more than what Windows could do without installing Wacom's driver package.

However, the cursor often misaligns such that bringing the stylus into the edges of the drawing area leaves the pointer somewhere along the way in the middle of the screen. Judging by the general feel of the movement, it seems as if there's a rounding error or some other inaccuracy when translating the stylus position into cursor acceleration, which makes attempts at drawing or any other kind of accurate control frustrating.

What could be the possible causes for this? A short poke with lsmod and modinfo tells me that the appropriate driver ('wacom') is loaded. dmesg, syslog and the X.org log files show no signs of shady business. FWIW, I'm also using Beryl on top of AIGLX, although I doubt it should have any effect on input devices.

---

### Post by tetsura on 2007-07-09
i just tried using my graphire 3 in ubuntu for the first time and im getting the same problem. 
sometimes the edge of the tablet is aligned with the edge of the screen, and then a few seconds later it could stop a few cm short of it or in the middle of the screen, its very strange. 
i looked at /etc/X11/xorg.conf and it seems to be recognised fine though :S

---

### Post by filologen on 2007-07-10
And I have the same problem with a Graphire 4 on my MacBook Pro running Feisty Fawn. Hope someone can help out :-)

---

### Post by Dragonbite on 2007-07-10
Is is more than just the tablet acting like a mouse (relational positioning) than a tablet (absolute positioning)?  

If you get to the edge of the tablet (in the middle of the screen) and you pick up the pen, move it backwards, bring it down on the tablet and continue sliding does the cursor continue in that direction?

There is also the [[COLOR="Blue"]WacomTableIssue[/COLOR]]("https://help.ubuntu.com/community/WacomTabletIssue") Wiki Page, though it doesn't look like it has this issue in it.

---

### Post by tetsura on 2007-07-10
well mine's using "absolute positioning"

---

### Post by Lorkki on 2007-07-11
> **Dragonbite said:**
> Is is more than just the tablet acting like a mouse (relational positioning) than a tablet (absolute positioning)?  


Actually it was a pretty simple problem, but a different one. I was missing the extended input devices from xorg.conf, probably because of my previous tweaking, so the tablet was handled through /dev/input/mice with a generic mouse driver. Apparently the default behaviour still is to approximate absolute positioning in this case, but accurate positioning and pressure data is lost.

To anyone else experiencing the same symptoms, try out the instructions here:
[https://help.ubuntu.com/community/WacomTroubleshooting]("https://help.ubuntu.com/community/WacomTroubleshooting") (note that the correct lines for USB devices are in the second code snippet)

---

### Post by galvheim on 2008-01-02
So this is still a open question?

I have the exact problem. Everything is installed correctly it seems, because both my xorg.conf files are setup to handle my graphire 4 and Gimp also recognize it. It works fine when i only use it as a mice, that means when the eraser, curseor and stylus is set in Gimp to not be active. Problem then is that all pressure-sensitivity is lost. So when I enable it to work on screen or window, then it will be misaligned by maybe 200 pixels. The cursor is there, but the brush is working at a diffrent place of the image I open.

If anyone can help to fix this that would be nice. I'm sure some of you have found a sollution.

---

### Post by galvheim on 2008-01-02
Developments: 

Well, I can give some more info on this. This is a problem that has mainly arised because I use a dual monitor setup. So when using the Options for the driver in xorg.conf like Twinwiew and ScreenNo i get into some quite exotic problems when using my tablet in the Gimp. See below:

> Section "InputDevice"
Driver "wacom"
Identifier "stylus"
Option "Device" "/dev/input/wacom"
Option "Stylus2" "3" # set button to right click
Option "Type" "stylus"
Option "USB" "on"
Option "PressCurve" "50,0,100,50" # Custom preference
# Option "Twinview" "horizontal"
# Option "ScreenNo" "1"
Option "Mode" "Absolute"
EndSection

In this it's excluded by the '#', because it simply doens't work. 
Problems can bee seen as the brush misaligning with the cursor when moving onto the workarea of a picture. I have also tried Twinview without specifying ScreenNo, then it let me chose screen automatically by letting the cursor jump over to the other screen when pushed to the edge of the screen. This also does not work, and the more I move from screen 0 the more offset it will become. 
Also when the brush is in close contact with the cursor in GIMP, the cursor will move much faster than the actual brush I use. So it's like a reversed servo or something. 

Only solution I can find so far is to disable the Twinview and ScreenNo completely and just work with my tablet on both monitors at the same time. In this situation I trust that my brain will automatically adjust itself to the weird aspect that follows this. 
I mean now my work area is stretched in the horisontal direction wheras it's the same in the vertical direction - being much faster in one direction than the other. And since my brain have not yet adjusted to this behaviour I draw elipses instead of circles at the moment.

No good. 

I would not sacrifice my dual monitor setup for such a redicilous bug. 

Too bad I don't know which one is the problem: GIMP or the Driver?

---

### Post by rudlavibizon on 2008-02-04
Hello, same problem here. Have you found the solution yet?
I made a workaround by letterboxing the pad by setting tracking to the appropriate aspect ratio. Please reply if you found out how can this be solved. It seems to be a Gimp issue.

---

