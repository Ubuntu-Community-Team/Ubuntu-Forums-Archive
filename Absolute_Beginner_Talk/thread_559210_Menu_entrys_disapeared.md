---
title: "Menu entrys disapeared"
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by jasonpeinko on 2007-09-24
My menu entrys dissapreared under applications except for office -> openoffice?!!? how do i get them back

---

### Post by Pumalite on 2007-09-24
Did you try rebooting?

---

### Post by jasonpeinko on 2007-09-24
just did and now nothing shows up. places and system work fine.

when i right click edit menu, only office and accesories are there.

---

### Post by Pumalite on 2007-09-24
Try re-installing your desktop.

---

### Post by RomeReactor on 2007-09-24
Hi. Try right-clicking on an empty space in your top panel, and select "Add to Panel" and add **Menu Bar**; now see if this menu works as it should. If it does, delete the old one and move this one to its place.

---

### Post by jasonpeinko on 2007-09-24
adding menu bar did not work and im reinstalling gnome now.

---

### Post by jasonpeinko on 2007-09-24
still nothing

---

### Post by bobplano on 2007-09-24
what about system menu>preferences>main menu? the system menu still worked you said, so maybe for some reason they just all so happened to get unchecked.

---

### Post by jasonpeinko on 2007-09-24
same thing, only accessories and office comes up.

---

### Post by jordanmthomas on 2007-09-25
I recently had a problem with my xdg variables not being set properly.  what is the output of this?
```
echo $XDG_CACHE_HOME;echo $XDG_CONFIG_DIRS;echo $XDG_CONFIG_HOME; echo $XDG_DATA_DIRS; echo $XDG_DATA_HOM
```

---

### Post by jasonpeinko on 2007-09-25
how do i start the terminal with alt+f2?

---

### Post by Pumalite on 2007-09-25
You have:
Alt+F2
and
Ctrl+Alt+F2 (Ctrl+Alt+F7 to get back to the window)

---

### Post by bobplano on 2007-09-25
ctrl+alt+F2 will get you to a terminal, but you could always do
alt+f2 then type xterm or gnome-terminal or konsole. xterm comes with all the *ubuntus

---

### Post by jasonpeinko on 2007-09-25
/usr/share/ubuntustudio-menu/

---

### Post by jasonpeinko on 2007-09-25
so what now?

---

### Post by jordanmthomas on 2007-09-25
Well, mine has a lot more:
```
/home/jordan/.cache
/etc/xdg
/home/jordan/.config
/usr/share:/usr/local/share
```

What is in the directory listed?
```
ls /usr/share/ubuntustudio-menu/
```
If it's more than just what is showing up on your menus than I don't know what is wrong.

However, if all that's in there is what's showing up on your menus than you may just need to set your XDG environment variables (not sure why it'd be unset though, mine was an issue between xlib and xproto I believe but I use ArchLinux and I haven't heard of such a conflict in Ubuntu)

So, I guess the next step is to find out what's in that directory compared to what's in your menu.

---

### Post by jordanmthomas on 2007-09-25
You may also find this link helpful
[http://ubuntuforums.org/showthread.php?t=559210&highlight=xdg](http://ubuntuforums.org/showthread.php?t=559210&highlight=xdg)

---

