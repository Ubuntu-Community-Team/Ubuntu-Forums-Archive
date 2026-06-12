---
title: "Weird... O.O"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by Hickler on 2007-07-11
This morning, I got up and happily booted up Linux, only to find that I had no connection. Upon further inspection, I realized that I didn't even have a wireless connection icon in the top right of my screen, and I could find no way to get to my wireless connections through the drop down menus. Can anyone help?

---

### Post by starcraft.man on 2007-07-11
Very weird. Did you do anything special before closing it the night before?

Try this to get the network manager started manually:

1) Push Alt + F2 to bring up the run box.

2) Type in "network-manager-gnome" and push enter. It should pop up and you should be able to select your wireless service.

If you use another one like wifi radar use the command that brings it up instead of network manager.

One thing you should check is sessions (System > Preferences > Sessions). Make sure that on the first tab your wireless manager is still set to launch at startup.

Best of luck with that :).

---

### Post by Inxsible on 2007-07-11
Go to the terminal and type in 
 
```
nm-applet
```unless you use some other wireless app

---

### Post by Hickler on 2007-07-11
Okay, thanks a lot, I'll boot to Linux now and hopefully I'll be able to post which one worked from there.

---

### Post by Hickler on 2007-07-11
Okay, I suppose this is good news, I booted into Linux, and I go to system>preferences>sessions first, I see that network manager is there and ticked, then all of a sudden, the bubble that tells you you have a connection appears on the left side of the screen (instead of the right where it normally is) and says I have a connection, and here I am. I find this strange because I have already tried rebooting... it just seems like my network manager icon is playing hide and seek with me!:)   But thanks for all the help anyway!

---

### Post by Hickler on 2007-07-11
Sorry for the back to back posts, but I'm realizing now that ALL my notifications are coming from the left side of the screen as if the icon is off screen somewhere. This is very annoying because for example when I run Kmess and I close it (but keep the app running) there is no way to restore it again except by going applications>internet>Kmess, the icon completely disappears, the same goes for amarok, and other apps. Has anyone had a similar experience or can anyone help?

---

### Post by Hickler on 2007-07-11
This problem has not been resolved, I have no connection once again and both neither of the solutions have worked, please help..

---

### Post by Hickler on 2007-07-11
Hehe, found the problem from another thread, kinda embarrassing actually, I just had to right click the panel, click add to and select notification area, :? Thanks for the help though.

---

