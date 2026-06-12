---
title: "Touchscreen Keyboard (OnBoard) issues and touchscreen right click"
date: 2015-04-24
forum: Assistive Technology &amp; Accessibility
---

### Post by zaileion on 2015-04-24
I am having 3 different issues with touchscreen controls on Ubuntu 14.10, 14.04 and 15.04.  (same issues with all 3 releases)

1.  I have activated OnBoard and configured it.  I've elected to use the option "Auto-Show when editing text" but this has problems...
     A.  When i touch the launchers top button "search" the keyboard doesn't pop-up
     B.  Chrome or FireFox among others doesn't pop-up keyboard.  No matter where i touch (address bar, google, any other search or text input bar.
     C.  This issue seems to randomly occur throughout different applications and/or locations throughout the system

2.  When i open different applications lets just use "System Settings" for example.  The keyboard automatically pops-up.  As my OnBoard settings suggest it should pop-up here since the search bar in "System Settings" is  automatically activated upon opening the application.  But i don't want the onscreen keyboard to open here.  How can i deactivate the search bar from automatically being active upon opening the program.  If i want to search i will touch the search bar then the keyboard should pop-up.  There should be a program that brings up a list of all programs installed on my computer allowing for me to select if the search or text input bar is automatically active or not, as well as if the onscreen keyboard automatically pops-up upon program launch.

It seems as though the OnBoard onscreen keyboard opens where it shouldn't but doesn't open where it should...  Maybe there is an onscreen keyboard application other than OnBoard that's more designed around touchscreen

As a kind of workaround for the 2 above issues i'm using the "show the floating keyboard icon" which allows for launching and hiding the keyboard with an (always on top) icon.

3.  Right Clicking without a mouse.  On other touchscreen OS's to open contextual menu or to "right click" one should touch and hold.  this feature is not available for me, removing the entire right click option unless i use a physical mouse.

Thanks for the Help.







**[SIZE=4][FONT=arial]*Quis custodiet ipsos custodes?*[/FONT][/SIZE]**

The inevitable truth is... Windows doesn't stand a chance...

---

### Post by Zyell002 on 2015-07-25
Hey.  I don't know if you are still having this issue, but I came across some of the same frustrations.  After much searching and trying a lot of different recommendations online, I finally wrote a script to fix the missing right click option when using a touchscreen.

From what I found, it looks like unity's multitouch control is deeply embedded and would require removal and subsequent recompile of unity before you could use a different multitouch system.  So I wrote a quick python script and tested it on both 14.04 and 15.04 with an ELAN touchscreen.  It seems to work pretty well.  It implements both a 2 finger tap and 1 finger long press to generate a right click.  You can find the script and instructions at [https://github.com/Zyell/Python-Touchscreen-RightClick](https://github.com/Zyell/Python-Touchscreen-RightClick)

As for Onboard, I haven't found an optimal solution for that one, and I have tried other keyboards with much worse results.  Moving from 14.04 to 15.04, onboard functions much better, but still not perfect.  

Anyway, hope that script helps if you are still having issues!

---

