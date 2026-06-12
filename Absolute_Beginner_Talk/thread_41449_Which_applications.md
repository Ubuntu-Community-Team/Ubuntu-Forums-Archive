---
title: "Which applications"
date: 2005-06-13
forum: Absolute Beginner Talk
---

### Post by ~J~ on 2005-06-13
Right, still enjoying my linux experience and stumped on the following questions.  Honestly I have tried to look rather than throw them in here without searching, but either the question yeilds a million results on google or I'm not asking the right question!

First up is the GRUB menu.  Is there a way for me to change the order of boot?  For example by default, Ubuntu is at the top, Windows XP is at the bottom.  For the time being, I'd like this swapped over and boot into Windows by default.  Any way of changing this.

I use blender.  The synaptic installer is saying that I can install version 2.36 but last week 2.37 came out and I can't seem to force the version.  If I use the windows version, it comes with a nice installer but the linux version seems to have everything in a package that I have to extract, whilst I don't really mind doing that, I don't really know where to put the files and would much sooner have a package installer.

KDE looks lovely, but I just think it's slooooooooow to use!  Gnome is fast, but has been hit with the ugly stick a few times.  Is there are tools that give the KDE look but in the Gnome environment.  I'd particularly like the applet bar with the fantastic RSS reader liek KDE has, and of course a few desktop gadgets like calendar, weather, etc, etc.  I've seen something called gDesklets but don't know if it's me being picky or not, but it looks kinda half-finished!

I've seen loads of screenshots with peoples "My computer" and their drives on the desktop.  How on earth are they doing that!  I've a mounted WIN32 drive that I have to traverse all around the file manager to get access to, having it on my desktop would be great.

And finally, bit of a silly one, but I'm really confused over it.  At gnomefiles.org their top file is something called ClearLooks ([http://gnomefiles.org/app.php?soft_id=810](http://gnomefiles.org/app.php?soft_id=810))  what on earth is it!  Is it just a variation of a theme?

Sorry for the questions, I'm sure others will have similar ones ;)

---

### Post by poofyhairguy on 2005-06-13
[QUOTE=~J~]
First up is the GRUB menu.  Is there a way for me to change the order of boot?  For example by default, Ubuntu is at the top, Windows XP is at the bottom.  For the time being, I'd like this swapped over and boot into Windows by default.  Any way of changing this.[/QUOTE]

Put this is terminal:

wget [http://www.freewebs.com/bored2k/grubconf_0.5.1-4ubuntu2_i386.deb](http://www.freewebs.com/bored2k/grubconf_0.5.1-4ubuntu2_i386.deb)

and 

sudo dpkg -i grubconf_0.5.1-4ubuntu2_i386.deb

---

### Post by bored2k on 2005-06-13
[QUOTE=~J~]KDE looks lovely, but I just think it's slooooooooow to use!  Gnome is fast, but has been hit with the ugly stick a few times.  Is there are tools that give the KDE look but in the Gnome environment?
[/QUOTE]
> 1. apt-cache search gtk qt
gtk-engines-geramik - Geramik GTK1.x Theme
gtk-engines-geramik-data - Geramik GTK Theme bitmaps
gtk-engines-qtpixmap - QtPixmap GTK1.x theming engine
gtk-engines-thingeramik - ThinGeramik GTK1.x Theme
gtk-engines-thingeramik-data - ThinGeramik GTK Theme bitmaps
gtk2-engines-geramik - Geramik GTK2.x Theme
gtk2-engines-gtk-qt - Makes your GTK 2 apps look like Qt ones
gtk2-engines-qtpixmap - QtPixmap GTK2.x theming engine
gtk2-engines-thingeramik - ThinGeramik GTK2.x Theme You just sudo apt-get install what you want, then go to system>preferences>themes and select them.

---

