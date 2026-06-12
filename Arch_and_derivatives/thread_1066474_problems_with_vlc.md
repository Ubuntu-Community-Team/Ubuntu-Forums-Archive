---
title: "problems with vlc"
date: 2009-02-10
forum: Arch and derivatives
---

### Post by stonecoldjha on 2009-02-10
hi everyone.i use vlc for playing my video files as well as a music player,but the one that is there in archgives me a lot of trouble.first of all the characters in the playlist as well as the bar that contains media,playlist,etc.gets distorted.please see the attached screenshots.

i recently uninstalled kde using
pacman -Rsn kde

now,vlc looks very ugly,though i did pacman -S qt4.vlc uses this interface,right?isn't there a way to make it use GTK as the interface,so that it can use my GTK theme?also,how do i solve the above problem?

---

### Post by SkonesMickLoud on 2009-02-11
-Rsn can be somewhat dangerous.  I personally would only use it to remove a package or two, versus removing the KDE group (many packages).

Have you tried reinstalling VLC?

---

### Post by handy on 2009-02-11
I always use VLC, but don't use KDE.

I don't have any problems at all with VLC.

---

### Post by SkonesMickLoud on 2009-02-11
> **handy said:**
> I always use VLC, but don't use KDE.

I don't have any problems at all with VLC.

It sounds like he removed some lib that VLC relies on.

---

### Post by handy on 2009-02-11
Are you using KDE or KDEmod?

I don't know, but, perhaps an easy way out would be to do a "pacman -Rsn vlc" followed by a "pacman -S vlc" 

It may be the simplest way to bring back into your system whatever has somehow managed to dissapear?

---

### Post by SkonesMickLoud on 2009-02-11
> **handy said:**
> Are you using KDE or KDEmod?

I don't know, but, perhaps an easy way out would be to do a "pacman -Rsn vlc" followed by a "pacman -S vlc" 

It may be the simplest way to bring back into your system whatever has somehow managed to dissapear?

Openbox, never had KDE on here.

A simple "pacman -S vlc" *should* grab any missing dependencies.  No need to completely remove anything that's about to be reinstalled.

---

### Post by handy on 2009-02-11
> **stonecoldjha said:**
> hi everyone.i use vlc for playing my video files as well as a music player,but the one that is there in archgives me a lot of trouble.first of all the characters in the playlist as well as the bar that contains media,playlist,etc.gets distorted.please see the attached screenshots.

i recently uninstalled kde using
pacman -Rsn kde

now,vlc looks very ugly,though i did pacman -S qt4.vlc uses this interface,right?isn't there a way to make it use GTK as the interface,so that it can use my GTK theme?also,how do i solve the above problem?

As far as I know, there is no longer support by VLC for GTK.

Is the  problem you are having related to font size?

---

### Post by handy on 2009-02-11
> **SkonesMickLoud said:**
> Openbox, never had KDE on here. 

I know, I use Openbox myself. :-)

[QUOTE=SkonesMickLoud;
A simple "pacman -S vlc" *should* grab any missing dependencies.  No need to completely remove anything that's about to be reinstalled.[/QUOTE]

Whatever you say boss.

It's ok, I'm a McLeod myself, I know why all the other clans pushed us onto the Isle of Sky. :-D

---

### Post by chucky chuckaluck on 2009-02-11
have you tried using qtconfig?

---

### Post by hrod beraht on 2009-02-11
> -Rsn can be somewhat dangerous.
It shouldn't be, because Pacman is too smartly designed. When doing recursive removals it will:
> Remove each target specified including all of their dependencies, provided that (A)** they are not required by other packages;** and (B)** they were not explicitly installed by the user**.

---

### Post by Open-SuSe-A-Me on 2009-02-11
Hey stonecold, would you mind sharing what gtk/compiz/emerald theme you use for the window borders?  It's quite fresh.

---

### Post by stonecoldjha on 2009-02-12
i use a GTK theme called "future".
[http://www.gnome-look.org/content/show.php/future?content=88170](http://www.gnome-look.org/content/show.php/future?content=88170)

but i have modified it slightly as the thread below says:
[http://ubuntuforums.org/showthread.php?t=1029437](http://ubuntuforums.org/showthread.php?t=1029437)

and the panel image that i use:
[http://www.gnome-look.org/content/show.php/Glass+Panel?content=46587](http://www.gnome-look.org/content/show.php/Glass+Panel?content=46587)

i use a beryl theme called venience shine:
[http://www.gnome-look.org/content/show.php/Vienniece?content=79431](http://www.gnome-look.org/content/show.php/Vienniece?content=79431)

i also use compiz-fusion to enhance the eyecandy.

i use an icon-theme called 0xy-gnome:
[http://www.gnome-look.org/content/show.php/oxy-gnome?content=79736](http://www.gnome-look.org/content/show.php/oxy-gnome?content=79736)

i also use a nice cursor theme called blue glass X cursors:
[http://www.gnome-look.org/content/show.php/Blue+Glass+XCursors+3D?content=5532](http://www.gnome-look.org/content/show.php/Blue+Glass+XCursors+3D?content=5532)


the only windowish thing i use is the beautiful segoeUI font.

---

