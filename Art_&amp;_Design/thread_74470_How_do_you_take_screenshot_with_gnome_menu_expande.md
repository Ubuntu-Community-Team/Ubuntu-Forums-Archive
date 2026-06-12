---
title: "How do you take screenshot with gnome menu expanded?"
date: 2005-10-11
forum: Art &amp; Design
---

### Post by idn on 2005-10-11
I want to take a screenie with the gnome menu expanded but it seems pressing the print screenbutton whilst having the menu expanded doesnt work. Does anyone have any ideas?

---

### Post by Buffalo Soldier on 2005-10-11
This may not be exactly what you want... but I guess you can try taking screenshot using GIMP. 

File -> Acquire -> Screenshot -> Whole Screen -> Grab

---

### Post by idn on 2005-10-11
Thanks, thats exactly what I wanted, you can specify after how many seconds you want t take it, so I had a chance to get the menu open, heres the screenie :)

[http://www.ubuntuforums.org/gallery/showimage.php?i=1089&original=1&c=2](http://www.ubuntuforums.org/gallery/showimage.php?i=1089&original=1&c=2)

---

### Post by darkmatter on 2005-10-11
[QUOTE=idn]I want to take a screenie with the gnome menu expanded but it seems pressing the print screenbutton whilst having the menu expanded doesnt work. Does anyone have any ideas?[/QUOTE]

You can run gnome-panel-screenshot on a timer. For example:

```
gnome-panel-screenshot --delay 5
```

Would wait five seconds before capturing your desktop. It will give you time to open your menu.

---

### Post by bdash on 2005-10-11
Or you can use Gimp to take your screenshot. You can add a timer.

---

### Post by aysiu on 2005-10-11
[QUOTE=darkmatter]You can run gnome-panel-screenshot on a timer. For example:

```
gnome-panel-screenshot --delay 5
```

Would wait five seconds before capturing your desktop. It will give you time to open your menu.[/QUOTE] When I was running Gnome, I created a keyboard shortcut for this very command. It came in handy.

---

### Post by bvc on 2005-10-12
sleep 5; gnome-panel-screenshot
(same thing)

If you have imagemagick;
sleep 5; import -window root -quality 91 ~/`date +%Y%m%d-%H%M%S`-lg.jpg
or simply
sleep 5; import -window root -quality 91 ~/screenie.jpg

---

