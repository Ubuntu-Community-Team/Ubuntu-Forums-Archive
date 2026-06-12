---
title: "Connecting to wireless networks in Xubuntu"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by rikc on 2007-07-09
I installed Ubuntu 7.04 on my laptop, and set up the drivers for my  Airlink USB 802.11g wireless adapter.  Later, as I am running on an older laptop, I installed Xubuntu 7.04.  Once I did this, I found that I was unable to connect to wireless networks in xfce, or at least that my adapter wasn't looking for them.  Xubuntu still recognizes the drivers as being installed, but I'm not sure how to directly look at my usb adapter and ask it to search for networks.  Strangely enough, if I log out and log back in on gnome, the internet connects with no problems, and if I log back into xfce after *that* the internet works fine.  Any ideas?

---

### Post by rikc on 2007-07-11
anyone?

---

### Post by ugm6hr on 2007-07-11
In Xubuntu - do you have the Network Manager applet working in the system tray (the thing you click on in Ubuntu to bring up a drop-down list of networks)?

If not - try this (in Xubuntu):
```
nm-applet
```
Then you should be able to connect, just as in Ubuntu.  Just make sure that the Network setting in Xubuntu says "roaming enabled". 

Xubuntu can cause a problem with multiple icons - if so - this will help:
[http://ubuntuforums.org/showthread.php?t=448952](http://ubuntuforums.org/showthread.php?t=448952)

PS: This should work, but if you want to remove GNOME dependencies, then Wicd is a much better option.  But it does require you to uninstall Network Manager.

---

