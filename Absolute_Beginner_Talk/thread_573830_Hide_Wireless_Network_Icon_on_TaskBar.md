---
title: "Hide Wireless Network Icon on TaskBar"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by syyid on 2007-10-12
Hi
I setup EduBuntu for a 4 yo nephew of mine except for the fact that he clicks on icon and removes the WEP key needing me to go in and reset it every other day. 
Is there a way to disable the icon or remove it from the task bar? If I right click on the clock there's an option 'remove from panel'. The wireless networks icon unfortunately doesn't have that. 

Also I was thinking there might be some privileges option where I could deny access to the network settings tools?

---

### Post by misfitpierce on 2007-10-12
I'm not sure if this will kill your connection as well closing the applet. If it does just restart computer and it will reload.

Terminal: 
pidof nm-applet
Then w/e number it comes up with ex. ?? do this
sudo kill ??

and it will close nm-applet which is the thing in bar for wireless control etc.

---

### Post by FuturePilot on 2007-10-12
You could create a new user as just a Desktop user. That user would not be able to access anything that requires root privileges. Which I'm guessing Network Manager falls under this category

---

### Post by LowSky on 2007-10-12
just get rid of the menu bars and make everything he might need into an icon, that might work... hope this makes sense because im wasted right now

---

### Post by naazgull on 2007-10-12
Hi,

Go to *System > Preferences > Session* and remove the entry that refers to Network Applet.

Cheers,

---

### Post by Incense on 2007-10-12
+1 for removing the network manager. Then you can connect using System - Admin - Network, and set up your wireless network there. I don't think it supports WPA (not sure though) but WEP is supported. Good job hooking them while they're young BTW!

---

### Post by syyid on 2007-10-14
> **naazgull said:**
> Hi,

Go to *System > Preferences > Session* and remove the entry that refers to Network Applet.

Cheers,


Thanks a lot everyone. Removing the network manager applet worked great and was specific to my nephew's user ID. 
On a side note, I got a bunch of applet errors on doing a switch user to another user id but this only happened the first time (A logout/login seemed to cure it)

---

### Post by hanzj on 2007-10-24
Will removing the network applet disable my wired internet connection?

---

