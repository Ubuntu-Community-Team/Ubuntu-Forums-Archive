---
title: "New Monitor: Resolution Issues?"
date: 2006-07-10
forum: Absolute Beginner Talk
---

### Post by petgraveyard on 2006-07-10
I just got a new monitor with a max screen resolution of 1280x1024 pixels.  I first started up with Windows, had the monitor automatically configure itself, and got it to work in 1280x1024.  I started it up in Ubuntu, and it looked magical.  However, I did find one problem after closer investigation.  When I went into the screen resolution, since it looked a bit large to me, I found that the monitor was on 1024x768.  I went in the dropdown to change it, and - this was the highest!  Is there anything I can do to make it so I can change my resolution to the maximum and recommended resolution (everything looks HUGE on this 19" LCD!)?  Thanks in advance for your assistance!

---

### Post by o_fortuna on 2006-07-10
It's a bit compilcated and messy to change resolutions on Ubuntu, but here goes.

Open up a terminal (Applications-->Accessories-->Terminal) and put this in:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
That should automatically configure it. The terminal screen will turn blue and it should show a screen with resolutions you can select. Use the arrows to move the cursor around and the space bar to select a resolution (you should see a star appear next to it). Press enter when you're done.

When the configuration is done, log out and, when you meet the login screen, press Ctrl-Alt-Backspace. The screen should blank and, if all is well, the resolution should be automagically configured. Or it should at least be changeable from System-Preferences-Screen Resolution.

---

### Post by Dr. Nick on 2006-07-10
Look at the first link in my signature, I have typed out the solution

[http://www.geocities.com/aebcoat/xorgresproblems.html?20069#Fix_low_resolutions](http://www.geocities.com/aebcoat/xorgresproblems.html?20069#Fix_low_resolutions)

---

