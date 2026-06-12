---
title: "update manager able to hide/ignore hide specific update?"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by NicoleM on 2007-04-17
i recently installed proprietary ATI drivers using the envy program and all seems to have worked well.  I now have the following listed as an update in my update manager:

fglrx-kernel-source
ATI binary kernel module source
from version 8.28.8-1 to 8.28.8+2.6.17.7-11.2 (Size: 685KB)

under the description it says 

This package builds the ATI XFree86 4.x/X.Org binary kernel module needed by xorg-driver-fglrx.
**This package is not needed on an Ubuntu system because a pre-compiled kernel module is supplied by the linux-restricted-modules packages. **

great...i don't need it.  aside from unchecking it each time i look at updates, is there a way to make the update manager ignore this particular update?

The reason it bothers me is because when i do a sudo apt-get upgrade it always shows up and I like being able to upgrade everything that needs to be upgraded in one shot as opposed to doing the apt-get command for each program that needs to be upgraded.

basically, my ATI drivers seem to be working fine, and I'm worried I'll accidentally install this and mess something up

---

### Post by NicoleM on 2007-04-17
apologize for bumping so soon was already almost to 4th page yikes :)

---

### Post by NicoleM on 2007-04-18
also as a secondary question (and shameless bump): if i can't set the update manager to ignore specific updates does anyone know if installing this update will ruin anything?

the ATI driver situation is a pain so I dont want to make it any more dificult than i have to

---

### Post by Sturmeh on 2007-09-22
I'd like an answer to this too...

Even windows has the functionality to hide specific updates. ( Surprisingly. xD )

I'm using wubi,to get the hang of linux, and the HAL updates break my usb capabilities, the new updates are really annoying me. ( I have to keep checking, its worse than it was on windows, i was hoping for "freedom" )

**EDIT:** I was wrong, it's there...

NicoleM, check Synaptic Package Manager ( as administrator ), make sure first the updates u don't want are on the update list ( in the notification bar ), then press the button ( in synaptic ) that sorts the packages by "marked/unmarked" the update-required will raise to the top...

Then select all ( Ctrl-click ? ) the updates you don't want to perform, and click "Packages>Lock Version" on the top menu.
Then check your updates again, and they are gone. xD

But REMEMBER you did this, it may cause you problems in the future. ( Better updates etc. )

---

