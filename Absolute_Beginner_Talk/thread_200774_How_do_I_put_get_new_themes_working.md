---
title: "How do I put get new themes working?"
date: 2006-06-20
forum: Absolute Beginner Talk
---

### Post by Amablue on 2006-06-20
I know how to change the themes that come packaged with Ubuntu, but I saw some on another site that looked good. I can't figure out how to get them to work though. I tried dragging the .tar.gz, the xml, and a few other files into the theme window but none of them worked.

---

### Post by user1397 on 2006-06-20
all you have to do is drag the .tar.gz file into the themes box (system > preferences > themes), so if it didn't work with the theme you downloaded, try another one because it really should work.

---

### Post by dmizer on 2006-06-20
first of all, are you trying to add metacity themes, or are you trying to add icon themes, or are you trying to add gtk themes?

gtk themes will change the look of your controlls, like menus and such.
metacity themes will change the look of your borders.
icon themes will of course change the look of your icons.

each of these are installed in different places.

there are others too, like gaim smiley themes and mouse pointer themes ... so what exactly kind of theme are you trying to install?

---

### Post by Trashbear on 2006-06-21
[QUOTE=dmizer]first of all, are you trying to add metacity themes, or are you trying to add icon themes, or are you trying to add gtk themes?

gtk themes will change the look of your controlls, like menus and such.
metacity themes will change the look of your borders.
icon themes will of course change the look of your icons.

each of these are installed in different places.

there are others too, like gaim smiley themes and mouse pointer themes ... so what exactly kind of theme are you trying to install?[/QUOTE]

I'm having the same issue while trying to drag a GDM theme into system>preferences>theme's window. Any help is greatly appreciated.

Edit: I'm using dapper if that means anything.

---

### Post by MaximB on 2006-06-21
you should drag the theme in the apropriate place
you can click edit on a theme in the theme category that already installed and there you can chose the icons metacity and etc...
try dragging the "zips" to there.
offcource you need the Gnome themes for ubuntu , or if you've changed it you'l know what kind of themes to put there

and there is very useful program you can install in the add/remove panel
that program let you chose what themes you want to install or save from the internet.
I forgot it's name but cheak for it.

---

### Post by dmizer on 2006-06-21
[QUOTE=Trashbear]I'm having the same issue while trying to drag a GDM theme into system>preferences>theme's window. Any help is greatly appreciated.

Edit: I'm using dapper if that means anything.[/QUOTE]
actually, the key here is that you're trying to load a gdm theme into a gtk theme window.  the system > preferences > themes selection is for the look of your desktop, not the look of gdm.

i've forgotten how to change gdm themes ... a search for "howto gdm theme" in this forum should produce results.

---

### Post by Bagnaj97 on 2006-06-21
To add GDM themes you need to go to System --> Administration --> Login Settings and you can drag and drop the tar.gz there.

A good way to find all kinds of Gnome themes (Icon, Metacity, GTK, Splash, GDM and wallpapers) is to install the gnome-art package from the repositories. It puts a gnome art menu entry in System --> Preferences

---

