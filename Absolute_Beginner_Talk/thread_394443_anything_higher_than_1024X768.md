---
title: "anything higher than 1024X768???"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by antgul3382 on 2007-03-26
like 1680X1050 - just got this new monitor

---

### Post by Raptor45 on 2007-03-26
```
sudo dpkg-reconfigure xserver-xorg
```

Run through that, and pick the correct resolution when that question comes.

---

### Post by antgul3382 on 2007-03-27
its asking me for a bus identifier?????? check it out, thanks for the help in advance

---

### Post by antgul3382 on 2007-03-27
please heeeeelp!!??!?!](*,)

---

### Post by antgul3382 on 2007-03-27
ok i went thru it all and its all good set to my resolution but its the same and the system>preferences>screen resolution  still says 1024X768

---

### Post by tipsqueal on 2007-03-27
Try using the official Nvidia drivers (non-free). That worked for me a while ago. You should be able to find out how to get them pretty easily, I don't really have time to look right now. If you have trouble just let me know and I'll get you a link, it should be relatively easy.

---

### Post by antgul3382 on 2007-03-29
it didnt work for me but i have a fresh install of feisty and its set correctly for the get go

---

### Post by v8YKxgHe on 2007-03-29
You do realize Feisty is only in Beta is isn't released for another month? If you're new to Linux/Ubuntu I highly suggest you do not use Feisty until it is released on April 19th.

---

### Post by tipsqueal on 2007-03-29
Another thing you can try is using the Xorg utility in the Nvidia drivers settings GUI. Just go to your menu, then go to system tools, then click on the Nvidia set up application (not sure what it's called I currently don't have a functional computer with Ubuntu). Somewhere within the program, I think the first or second tab on the left deals with the Xorg settings. One of them gives you an option to create a specific xorg for your gfx card and set up. Do this but save it to the desktop, then after it's made look at it, make sure it looks right, then back up your old xorg, then overwrite it with the one the utility made. That worked for me when I was having resolution issues with my login screen and normal desktop.

Hope I could help.

---

