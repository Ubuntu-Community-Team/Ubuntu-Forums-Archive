---
title: "Changing trash icon"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by SnotRocket on 2007-04-04
Ok this is driving me crazy.  I did a search to find all instances of trash in the filesystem.  I changed every user-trash.png or user-trash.svg and the full equivalents to the mac OSX trashbin icon.  Then I used killall gnome-panel to restart the panel and change the icon, but to no avail.

Where are the directories and filenames for the files that I need to change to have effect on the bar?

---

### Post by oilchangeguy on 2007-04-04
why is this important? the trash icon is in the lower part of the screen, hardly visable. why waste time on something like this???????????

---

### Post by land0 on 2007-04-04
It should just be a matter of changing the icon for it in the icon folder for the set you are using. It should be located at /usr/share/icons

---

### Post by land0 on 2007-04-04
> **oilchangeguy said:**
> why is this important? the trash icon is in the lower part of the screen, hardly visable. why waste time on something like this???????????

Because you can! :) ;) :guitar:

---

### Post by SnotRocket on 2007-04-12
Yes, and because I don't like the default trash icon.  I'd rather have something more visually appealing (I've been doing a mac OS look for my current theme, and editing the icons in the gnome taskbar is pretty annoying).

---

### Post by Brendantb on 2007-04-12
Hi, 

once you have changed all the icons for trash full and trash empty in the /Tango theme folders, you have to update the icon cache. 

Code:

sudo gtk-update-icon-cache -f -t /usr/share/icons/<theme-name>

Information gleaned from the Xfce wiki, hints and tips. 

Edit: I have just realised that you are using Ubuntu, not Xubuntu. The code may be different for you, I don't know, but you will still have to update the icon cache. You may need to look about in the Gnome Desktop wiki to find the correct formulation.

---

