---
title: "Anyway to make utorrent look nicer?"
date: 2007-04-29
forum: Art &amp; Design
---

### Post by super.rad on 2007-04-29
I've just installed utorrent through wine but it looks really ugly, i was wondering if their was anyway i could make it fit in better with gnome (eg are their any gnome themes for utorrent)

---

### Post by junior aspirin on 2007-04-29
run 'winecfg' click the 'desktop integration' tab.

from here you can install a windows theme from deviantart/windows/wherever (warning! will slow wine down)

what i do is manually change the colours of the 'item' drop down. unfortunately there is no colour picker in wine. To get the exact colour codes open the wallpaper changer in Gnome then the background colour button at the bottom. now you have a colour picker.
use the colour picker to find out the colour codes used in your theme.
transfer the hue/sat/value/red/green/blue across to the wine colour controls

here is what i changed in the winecfg tab:
controls background > window bg colour
Menu background > the menu bar colour (same as above usually)
Selection bg > highlight colour

then click apply and restart the windows application. and look how nice it looks


edit: also you can change the icons to tango/human 
go to [http://utorrent.com/skins.php](http://utorrent.com/skins.php)
the download the bmp to '~/.wine/drive_c/windows/profiles/paul/Application Data/uTorrent'


it looks allot of work, but it takes seconds. hope it makes sence.

---

### Post by zgornel on 2007-05-02
Try rufus instead. It is fast and very utorrent-like.

---

### Post by aidanr on 2007-05-02
there's also a how-to, with a utorrent theme to match human a few posts down
[http://ubuntuforums.org/showthread.php?t=142741&highlight=how+to+make+wine+look+better](http://ubuntuforums.org/showthread.php?t=142741&highlight=how+to+make+wine+look+better)

---

