---
title: "Enlightenment and Gnome"
date: 2005-11-08
forum: Absolute Beginner Talk
---

### Post by zerhacke on 2005-11-08
I use Enlightenment quite a bit.  In my application menu I have set nautilus as an application I can open.

Interestingly enough, the moment I open nautilus, the shortcuts I have placed on my Gnome desktop appear, along with my Gnome wallpaper.

Is this normal?

---

### Post by jasay on 2005-11-08
Yes it is.  Change the command line of nautilus lanucher to ```
nautilus --no-desktop --browser %U
```  That way you don't load the desktop, only the browser.

---

### Post by Kyral on 2005-11-08
I actually think it is. I believe that Nautilus in GNOME is responsible for more than the file management, or to put it better, since the desktop is treated like a folder (its actually the Desktop folder in your homedir), when Nautilus loads, it also loads the settings it knows for the Desktop folder.

I hope that makes sense..

---

### Post by jasay on 2005-11-08
Thanks for the explanation Kyral, I alwasy wondered why it did that.  Makes sense to me.

---

### Post by zerhacke on 2005-11-09
[QUOTE=jasay]Yes it is.  Change the command line of nautilus lanucher to ```
nautilus --no-desktop --browser %U
```  That way you don't load the desktop, only the browser.[/QUOTE]
That worked fine.  Thanks for the command.

The explanation given by Kyral explains it well.  I believe it's worth more than just a file manager myself now.  Now all we have to do is figure out where the settings for the Desktop folder are stored in order to tinker with them.

Using the regular command "nautilus" one can get an Gnomed Enlightenment versus an Enlightened Gnome.

---

### Post by varunus on 2005-11-09
You may already know this, but just a tip:  if you want to "gnome" enlightenment, make sure to load the program "gnome-settings-daemon" before you launch gnome apps.  This will make your gnome font, icon, and gtk theme preferences stick in enlightenment; it will also let you use many of the gnome configuration tools in enlightenment itself.  (I believe nautilus will show blank icons for everything if gnome-settings-daemon is not loaded.)

Good luck.

---

