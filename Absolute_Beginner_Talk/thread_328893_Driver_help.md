---
title: "Driver help"
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by FarthestStar on 2006-12-31
I've been trying to get xgl to work on my HP dv5140us and getting my Radeon Xpress 200M to work for that. I've tried following the instructions at [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide"), but I ended up getting a blank screen and could not figure out how to edit xorg.conf in the recovery mode.

So, I started over with a fresh install of Dapper and now I'm trying to update drivers at [http://ati.amd.com/support/drivers/linux64/linux64-firegl.html]("http://ati.amd.com/support/drivers/linux64/linux64-firegl.html").
I tried to run Check.sh from the Desktop to figure out what I need to download, but I end up getting:

=========================================
 ATI Technologies
=========================================
You are either not running this script from the console
or simply do not have console ownership.  Requirement failed.
Unable to determine XFree86 Version. Stopping now.


Can someone tell me what do I have to do to get the scrip to run correctly and if I'm moving in the right direction for setting Xgl?

Thanks in advance.

---

### Post by jem7v on 2006-12-31
If you try to run the script from the desktop and it says you aren't in a console, that's because you're running it from the desktop. Ctrl+Alt+F(1 through 6) will take you to a virtual console where you can run the script outside the desktop environment. Ctrl+Alt+F7 should probably bring you back to your desktop.

As for doing XGL on that Radeon? I don't know if that's a good idea, because I've heard ATI's Linux drivers have... issues... and it'll really chug, even on their good cards. I could be wrong, though! Also, it might be easier to run a composite desktop in Edgy than in Dapper.  I'm using Edgy and it was pretty darn simple to set up.

As for editing xorg.conf from a command line, try using nano... i.e.,

```
sudo nano /etc/X11/xorg.conf
```

---

### Post by FarthestStar on 2006-12-31
I got to the console with ctrl+alt+f1 and ran the script, but I still get the same output.

---

### Post by jem7v on 2006-12-31
Did you use sudo? Administrative tasks run through the console need to start with the sudo command to give it the proper priviledge to do its thing... i.e.,

sudo commandgoeshere

---

### Post by FarthestStar on 2006-12-31
I used 

sudo sh check.sh

in the console and I'm still getting that error.

---

### Post by jem7v on 2006-12-31
Wull, I'm not sure what to suggest then. Have you tried looking for that error on Google? Sometimes that'll find you an answer quicker than waiting for someone here to know what's going on.

Btw, the reason I suggested trying it in Edgy instead of in Dapper is because Edgy uses the latest version of xorg (7.1) and Dapper still uses 7.0, and 7.1 has much better support for XGL and all those other composite managers out there. [https://help.ubuntu.com/community/CompositeManager](https://help.ubuntu.com/community/CompositeManager) has a little bit of information about it if you haven't seen it yet.

Sorry I couldn't have been more help!

---

