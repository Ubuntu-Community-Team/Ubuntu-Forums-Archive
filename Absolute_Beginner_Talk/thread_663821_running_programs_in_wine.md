---
title: "running programs in wine"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by chips24 on 2008-01-10
how do you run somthing in wine?

---

### Post by yabbies on 2008-01-10
depends on what you want to run

---

### Post by philinux on 2008-01-10
If say you got a setup.exe file onto your desktop. With wine installed double clicking the exe wine will "attempt" to install it for you.

---

### Post by JacobRogers on 2008-01-10
Try using Wine Doors, it looked really cool and usful last time I looked at it.  I don't have any windows software I need to run so I'm not that good with wine.

---

### Post by chips24 on 2008-01-10
thanks, ill try

---

### Post by Hospadar on 2008-01-10
from a command line, cd to where the executable is located (if it's on your desktop, it'd be like cd ~/Desktop) and then do "wine <filename>.exe"

You can get a terminal from Applications->Accessories->Terminal

You could also create a launcher who's command is something like "wine /path/to/file/executable.exe" and double click that.

You can just double-click executables, but in wine it's often nice to see the terminal output as it can help you sort out problems if things don't run right.

If you want to learn a little more about basic terminal navigating and commands, google something like "basic linux command line tutorial" and you'll find whole bunches of stuff

Also, the commands "winecfg" and "uninstaller" provide some useful setup options, as well as an uninstaller, you can also do "regedit" to get a registry editor just like the one in windows (some apps require registry tweaks to get working) If you are trying to get a specific app working, search for it in the wine appdb (found on the main wine website) they have pages for most commonly used windows applications (especially games)

Happy wining ;-)

---

