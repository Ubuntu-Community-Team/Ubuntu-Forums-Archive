---
title: "[SOLVED] Compiz Fusion in Arch Linux with Xfce... :("
date: 2009-01-02
forum: Arch and derivatives
---

### Post by gjoellee on 2009-01-02
I installed ```
pacman -S compiz-fusion-gtk
``` however Emerald wont work at all leaving my windows without a border. Dragging windows with the alt button presses and closing and opening them in the panel sucks, and I don't want it like that.

I use Xfwm4 at the moment, and this leaves me without any cool effects. Got eny ideas abotu how to install Compiz Fusion in Xfce and make it work properly?

---

### Post by crimesaucer on 2009-01-02
> **gjoellee said:**
> I installed ```
pacman -S compiz-fusion-gtk
``` however Emerald wont work at all leaving my windows without a border. Dragging windows with the alt button presses and closing and opening them in the panel sucks, and I don't want it like that.

I use Xfwm4 at the moment, and this leaves me without any cool effects. Got eny ideas abotu how to install Compiz Fusion in Xfce and make it work properly?

There is the compiz-fusion icon, I think it it is in the system tray (which won't work with that patched xfce4-panel.... so fix emerald first then install that patched panel after compiz/emerald is you default window manager).

Anyway, you need to right click it and select "Emerald" as your default window manager.

Then you will want to add compiz-fusion to your auto-started apps: [http://wiki.archlinux.org/index.php/Compiz-Fusion#Xfce_autostart_.28without_.22compiz-fusion.22.29](http://wiki.archlinux.org/index.php/Compiz-Fusion#Xfce_autostart_.28without_.22compiz-fusion.22.29)


You could also try this command to run it for only 1 session (type alt + f2):

```
emerald --replace
```

(I think that's the correct command)

---

### Post by gjoellee on 2009-01-02
I launched emerald in the terminal instead and got this error: 
```
/home/zippex/.gtkrc-2.0:6: Unable to locate image file in pixmap_path: "bg.png"

``` so it reacts on a picture from the .gtkrc-2.0 file. Then I checked that file and i looks like this:
```
 style "panel-background" {
   bg_pixmap[NORMAL]        = "bg.png"
   bg_pixmap[PRELIGHT]      = "bg.png"
   bg_pixmap[ACTIVE]        = "bg.png"
   bg_pixmap[SELECTED]      = "bg.png"
   bg_pixmap[INSENSITIVE]   = "bg.png"
 }
 widget_class "*Panel*" style "panel-background"
```

is this the panel cairo patch? obviously there is a png file missing.

---

### Post by gjoellee on 2009-01-02
I made a bg.png my self and it did not work. so It is not that. I also tried blanking the file logged out and logged in, still the same.... no worries, I don't need compiz...

---

### Post by crimesaucer on 2009-01-02
> **gjoellee said:**
> I launched emerald in the terminal instead and got this error: 
```
/home/zippex/.gtkrc-2.0:6: Unable to locate image file in pixmap_path: "bg.png"

``` so it reacts on a picture from the .gtkrc-2.0 file. Then I checked that file and i looks like this:
```
 style "panel-background" {
   bg_pixmap[NORMAL]        = "bg.png"
   bg_pixmap[PRELIGHT]      = "bg.png"
   bg_pixmap[ACTIVE]        = "bg.png"
   bg_pixmap[SELECTED]      = "bg.png"
   bg_pixmap[INSENSITIVE]   = "bg.png"
 }
 widget_class "*Panel*" style "panel-background"
```

is this the panel cairo patch? obviously there is a png file missing.

This is difficult to understand.


So you are getting an error about your panel and you panel gtkrc-2.0 when trying to run emerald window manager that shouldn't have anything to do with the panel?


Did you check to make sure your bg.png exist in your home folder? 


Also, did you try running the command that I gave you in the "alt + f2" app for running a program?


Have you tried not using the ~/.gtkrc-2.0 for a moment until you get everything working properly..... it might have something conflicting with the your panel and emerald..... also what panel plugins are you using.... it might be either the "System Tray" or "Icon Box" panel-plugins..... neither of those work properly with the patched xfce4-panel.

---

### Post by gjoellee on 2009-01-19
I really solved the problem now! I found this WIKI: [http://wiki.archlinux.org/index.php/Composite](http://wiki.archlinux.org/index.php/Composite) 

I just had not configured Xorg correctly

---

