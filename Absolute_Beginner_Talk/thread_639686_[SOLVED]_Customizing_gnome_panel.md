---
title: "[SOLVED] Customizing gnome panel"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by OttoDestruct on 2007-12-13
I was wondering how to go about getting rid of the text on the gnome panel ("Applications" "Places" "System"), and actually merge Places and System just into one menu.

This screenshot has an example of what I want to do (its a screenshot for a theme, I don't care about the theme, I just want to make the gnome panel function like it is set up however)

[http://gnome-look.org/CONTENT/content-pre1/44495-1.jpg](http://gnome-look.org/CONTENT/content-pre1/44495-1.jpg)

---

### Post by mocoloco on 2007-12-13
Easy as pie.  Your three section menu is just another applet on the panel, it's called the "Menu Bar".  There's another menu applet simply called "Main Menu" that does what you're describing.  Right-click an empty area in the panel and add the main menu applet.  Remove the other menu simply by right-clicking on it and selecting "remove from panel".

---

### Post by OttoDestruct on 2007-12-13
> **mocoloco said:**
> Easy as pie.  Your three section menu is just another applet on the panel, it's called the "Menu Bar".  There's another menu applet simply called "Main Menu" that does what you're describing.  Right-click an empty area in the panel and add the main menu applet.  Remove the other menu simply by right-clicking on it and selecting "remove from panel".

Thanks a bunch. Second question: How can I change the image of it? Theres an ugly little black arrow which I'm assuming is just part of some .gif or something somewhere.

I hate being annoyed by the small details :( I can never get anything accomplished until things are "just right"

---

### Post by philinux on 2007-12-13
And if you put Main Menu in the bottom left - what does this remind you off .....

---

### Post by SunnyRabbiera on 2007-12-13
> **philinux said:**
> And if you put Main Menu in the bottom left - what does this remind you off .....

well hey Linux has been doing it longer then windows has.

---

### Post by OttoDestruct on 2007-12-13
> **philinux said:**
> And if you put Main Menu in the bottom left - what does this remind you off .....

The same could be said for all the people putting on dock panels :)

It works, and works well, its just what I happen to prefer. Until Gnome does something better I'll stick with what I know.

Edit: Still would appreciate an answer for my second question above

---

### Post by skrribble on 2007-12-13
> **OttoDestruct said:**
> Thanks a bunch. Second question: How can I change the image of it? Theres an ugly little black arrow which I'm assuming is just part of some .gif or something somewhere.

I hate being annoyed by the small details :( I can never get anything accomplished until things are "just right"

find an icon you want to replace it with and name it gnome-main-menu.png and put it in your /home/yourname/.icons/yourtheme/scalable/places folder.  then restart your theme by switching it to something else then swtiching it back.... that should do it

---

### Post by OttoDestruct on 2007-12-13
> **skrribble said:**
> find an icon you want to replace it with and name it gnome-main-menu.png and put it in your /home/yourname/.icons/yourtheme/scalable/places folder.  then restart your theme by switching it to something else then swtiching it back.... that should do it

Thanks.

---

### Post by OttoDestruct on 2007-12-13
Seems I thought this was solved prematurely - when I go to drop the image in that folder I can't get past /.icons   -  theres nothing inside that folder :confused:

---

### Post by skrribble on 2007-12-13
Are you using one of the themes that is on the computer by default???
if you are then those themes are at /usr/share/icons

you will need to have root privelages to paste into this folder, so do a
```
gksudo nautilus
```
and then browse to the folder of your current theme, then paste it in /scalable/places and restart the theme... sorry about the mix up before, i'm used to having people asked about themes they installed themselves

check out [http://www.gnome-look.org](http://www.gnome-look.org) for icon themes made by other people

---

### Post by mocoloco on 2007-12-13
Hate to crash the party, but I don't think that little arrow is part of the png, if you move the menu to the bottom panel, side panel, etc it moves the arrow.  Getting rid of it may be a bit more complicated.

---

### Post by GeorgiaBoot on 2007-12-13
If you have installed your own theme got to /user/.icons/theme/places/scalable

Find the image that says (start-here.png) then replace it with your image.

Make sure to name your image start-here.png, also make it a png image.

Also remember under User you need to hit Ctrl+H to show the hidden icons.

Goodluck

---

