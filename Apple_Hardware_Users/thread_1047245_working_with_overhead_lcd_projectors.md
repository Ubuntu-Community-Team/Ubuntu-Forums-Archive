---
title: "working with overhead lcd projectors"
date: 2009-01-22
forum: Apple Hardware Users
---

### Post by goneskiing on 2009-01-22
I'm running 8.10 on a white macbook - trying to use with overhead lcd  projectors in the classroom - no luck.  We have NEC and Epson projectors.  When I reboot I see the Ubuntu logo - then it loses signal.  When I try to run xrandr --auto I get an error "missing crtc".  Please help - I need this to teach well.  ps: I only have unbuntu on this machine, no OSX.

---

### Post by wangsuda on 2009-01-22
I have almost the same problem! I run 8.10 on an Acer Aspire 3680 and need to display on an LCD. I have gotten as far as -system/preferences/screen resolution, but getting my computer's image onto the LCD display is still beyond me. Help is appreciated.

---

### Post by wangsuda on 2009-01-23
OK, I figured it out! Here's what you do:
1.Go to system>preferences>screen resolution. Click on the icon. A dialogue box will open.
2.Click on &#8220;detect displays.&#8221; At this point, you should see your computer and something else called &#8220;unknown device.&#8221;
3.Single click on the unknown device. Then, set the screen resolution from the drop down menu to its highest setting.
4.Single click on your computer. Set the screen resolution to the same setting as the unknown device. At this point, both boxes should be the same size.
5.Tick the box in the upper left corner that says &#8220;mirror device.&#8221;
6.Your computer will reset itself. This should take about 10-20 seconds. You might have to re-enter your user name and password.

If everything went well, the LCD should be projecting exactly what is on your laptop's LCD.

Good luck!

---

### Post by goneskiing on 2009-01-30
also these 2 commands seem to do it though screen keeps resetting every 20 seconds or so

xrandr --output TMDS-1 --off
xrandr --output VGA --auto

---

