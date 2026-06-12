---
title: "Getting back the foot icon. :)"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by alex-desktop79 on 2007-06-16
I was wondering how to restore the Gnome foot icon in the upper left pannel. The menu bar.

---

### Post by alex-desktop79 on 2007-06-16
bump

---

### Post by alex-desktop79 on 2007-06-16
bump again. I'm sure this is extreamly simple.

---

### Post by forestpixie on 2007-06-16
not sure if I've got this - are you trying to get the menu bar back??

If so - right click top panel - add to panel and add the menu bar - it's right at the bottom. If not not sure what you want - but at leasty you won't feel lonely!

:)

---

### Post by alex-desktop79 on 2007-06-16
No. I'm trying to change the ubuntu icon in the menu for the gnome foot. :)

---

### Post by testube_babies on 2007-06-16
It depends what icon theme you are using.

So, what icon theme are you using and where is it located?  You have to replace the distributor-logo icon file (or files) in your icon theme with a gnome foot icon.

---

### Post by alex-desktop79 on 2007-06-16
I'm using nuove-XT, installed it by dragging and dropping the .tar.gz

---

### Post by testube_babies on 2007-06-16
These commands should do it:
```
sudo mv /usr/share/icons/hicolor/48x48/apps/distributor-logo.png /usr/share/icons/hicolor/48x48/apps/distributor-logo_old.png
sudo cp /usr/share/pixmaps/gnome-about-logo.png /usr/share/icons/hicolor/48x48/apps/distributor-logo.png
```


To restore the Ubuntu logo:
```
sudo mv /usr/share/icons/hicolor/48x48/apps/distributor-logo_old.png /usr/share/icons/hicolor/48x48/apps/distributor-logo.png
```

If that doesn't work, try this (there is no undoing this unless you back up these files first):
```
sudo cp /usr/share/pixmaps/gnome-about-logo.png /usr/share/icons/gnome/16x16/places/distributor-logo.png
sudo cp /usr/share/pixmaps/gnome-about-logo.png /usr/share/icons/gnome/22x22/places/distributor-logo.png
sudo cp /usr/share/pixmaps/gnome-about-logo.png /usr/share/icons/gnome/24x24/places/distributor-logo.png
sudo cp /usr/share/pixmaps/gnome-about-logo.png /usr/share/icons/gnome/32x32/places/distributor-logo.png
sudo cp /usr/share/pixmaps/gnome-about-logo.png /usr/share/icons/gnome/scalable/places/distributor-logo.svg
```

If the icon is the wrong size, you'll have to resize it in the GIMP.

---

### Post by alex-desktop79 on 2007-06-16
Edit: In the ad panel window the icon has correctly changed, but when I place the panel it's still the ubuntu logo.
Edit2: The Main menu item has a gnome foot but still not the Menu Bar item.

---

### Post by pistcivet on 2007-06-16
You say the icon theme is nuove-XT.
So its probably in ~/.icons/nuove-XT/

You'll have to find and replace start-here.png which should be a
symbolic link of distributor-logo.png.
(distributor-logo.png is a link to start-here.png)
Try looking in ~/.icons/nuove-XT/48x48/places/  (or similar).

Then you should rebuild the icon cache and restart the display manager:
```
gtk-update-icon-cache ~/.icons/nuove-XT
killall gnome-panel
```

I think that will do it.
I messed up that code. It should be killall gnome-panel. Sorry!

---

### Post by testube_babies on 2007-06-16
hmmm...

You might want to fish around in /usr/share/icons/gnome to see if there are other distributor-logo files that I missed.  The commands I gave above worked for my setup, so I'm not sure what else to do.

---

### Post by alex-desktop79 on 2007-06-16
I tried changing my icon theme to every other one possible. And it always kept the exact same icon. So I dont think that's the issue.

---

### Post by pistcivet on 2007-06-16
How about you try this icon theme:
[http://www.gnome-look.org/content/show.php/Ubuntu_HumanAzul?content=37099](http://www.gnome-look.org/content/show.php/Ubuntu_HumanAzul?content=37099)

It turned my distributor-logo blue.
Can you get yours to change at all?

---

### Post by testube_babies on 2007-06-16
You just have to find the right file to replace...as we have seen it can be tricky.

Try this out to list them all:
```
sudo updatedb
locate distributor-logo
```

---

