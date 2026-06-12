---
title: "theme"
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by cmaranhao on 2006-10-04
i want to install a new theme for linux 6.06 but it asks for a location.. i said a locations (/home/username/theme ) but it said its invalid

what should i put for theme location?

---

### Post by jaboua on 2006-10-04
What theme are you trying to install? What kind of package and for what app?

---

### Post by jordanmthomas on 2006-10-04
First, what kind of theme have you downloaded?

If you have downloaded the theme to your Desktop, just drag it onto the main theme window.  (if it is a metacity / gtk / icon theme only)
If that doesn't work and it it is one of those themes (see above), open the theme package and then press Alt + F2
type
```
~/.themes
```
or
```
~/.icons
``` in the case of an icon theme

drag the folder within the archive to this folder, and the theme will have been installed.

---

### Post by cmaranhao on 2006-10-04
i want the silicon theme

---

### Post by jordanmthomas on 2006-10-04
```
sudo apt-get install silicon-theme
```

Then, it will be in the themes dialog.

---

### Post by Over1ord on 2006-10-04
Where can you get more themes from?

---

### Post by jordanmthomas on 2006-10-04
I like [http://www.gnome-look.org](http://www.gnome-look.org)
There is also
[http://art.gnome.org](http://art.gnome.org)

Take a look through Synaptic and there are themes (gtk-theme-*)

---

### Post by cmaranhao on 2006-10-04
> maranhao@maranhao-desktop:~$ sudo apt-get install silicon-theme
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package silicon-theme

that did not worked..more help is required

---

### Post by jordanmthomas on 2006-10-04
D'oh!  It's not in Dapper.

You can get it from here, though
[http://packages.ubuntu.com/edgy/x11/silicon-theme](http://packages.ubuntu.com/edgy/x11/silicon-theme)

Download it (click on the word 'all') and then double click it to install.

If it still doesn't work, post back

---

### Post by cmaranhao on 2006-10-04
download it.. clicked 2 times for instalation and it gives me an error..

error: conflicts with the installed package 'ubuntu-artwork'

---

### Post by jordanmthomas on 2006-10-04
Okeydokey, try this then.
drag this link onto the theme window.
[http://jordanmthomas.googlepages.com/Silicon.tar.gz](http://jordanmthomas.googlepages.com/Silicon.tar.gz)

---

### Post by cmaranhao on 2006-10-04
worked like a charm. thanks mate:cool:

---

### Post by jordanmthomas on 2006-10-04
No problem.  That certainly turned out to be more complicated than the standard theme install, so don't be turned off by it.

---

