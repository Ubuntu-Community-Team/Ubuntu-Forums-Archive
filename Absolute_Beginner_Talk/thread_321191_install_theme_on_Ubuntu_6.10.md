---
title: "install theme on Ubuntu 6.10"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by lucky_chouhan on 2006-12-18
hi i want to know how to install kde themes from [http://www.kde-look.org/](http://www.kde-look.org/)

i am try several themes but he can not recognise theme.

any people tell me what is the exact procedure to install them on my ubuntu 6.10.

:(

---

### Post by Rackerz on 2006-12-18
When you download a file it should be a tar.gz, don't open it, just point the themer to it.

---

### Post by d3v1ant_0n3 on 2006-12-18
As said above, the easiest way to install themes is to either drag them into the 'theme' window, or point to the file using the 'install new' button. You *might* have to extract the folder, then place it manually into the .themes folder inside your home directory (the . means its a hidden folder, so you'll have to show hidden folders first).

Silly question, but you *are* running KDE? I made this mistake once...;)

---

### Post by lucky_chouhan on 2006-12-18
hi Rackerz i open the theme manager and locate the theme file without extract. bt he dosn't recognize. what i do.

---

### Post by Pobega on 2006-12-18
You have to be running KDE to use KDE themes.

For Ubuntu (Default Gnome) themes see [http://gnome-look.org/](http://gnome-look.org/)

---

### Post by lucky_chouhan on 2006-12-18
thank for the link some time for testing.

so these all themes support on ubuntu os.

---

### Post by lyceum on 2006-12-18
> **lucky_chouhan said:**
> thank for the link some time for testing.

so these all themes support on ubuntu os.

Yeah, Ununtu is Gnome, Kubuntu is KDE, Xubuntu is XFCE. The "  "-look.org is not the only option for Gnome, you can try gnome-art.org too.

---

### Post by Pobega on 2006-12-18
Technically you can have them all on one distro though, just run

[code]sudo aptitude install ubuntu-desktop
sudo aptitude install kubuntu-desktop
sudo aptitude install xubuntu-desktop[/url]

Then install the theme to the appropriate Window Manager.

---

### Post by d3v1ant_0n3 on 2006-12-18
Themes on [www.gnome-look.org](www.gnome-look.org) are for GNOME desktops- Ubuntu. 

The GTK+ themes will change the appearance of windows, their colors etc, and the look of panels and buttons.

The Metacity themes will change the look of your window borders.

The GDM themes will change the look of your login screen.

Icons Themes will change the icon set (but not always ALL of them).

etc.

Themes of [www.KDE-look.org](www.KDE-look.org) are for KDE desktops (Kubuntu).

Styles will change the appearance of windows.

Color schemes will change the color theme used in all (KDE based) apps

Window Decorations will change the window borders.

Themes are generally not interchangable between KDE and GNOME (exceptions are wallpapers and X11 mouse themes)

Have fun! There's SO many possibilites for customizing the look of your Ubuntu.:D

---

