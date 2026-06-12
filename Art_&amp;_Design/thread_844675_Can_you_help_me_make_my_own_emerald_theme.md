---
title: "Can you help me make my own emerald theme?"
date: 2008-06-29
forum: Art &amp; Design
---

### Post by TommyIndep on 2008-06-29
I want to be able to create my own emerald theme, not just edit the ones I've got already, but start from scratch, can anybody please help me with this? Which programs do I need? Stuff like that. Thanks a bunch!

---

### Post by TommyIndep on 2008-06-29
Please, anybody?

---

### Post by Cherry Cotton on 2008-06-30
Hmm, I ventured once into trying to make my own theme... here's what I remember...

Basically, there are two parts... there's the GTK theme, which determines what the window contents look like, like toolbars, menus, buttons, stuff like that. Then, there's the Metacity theme, determining the look of the window border.

Within the GTK theme, there's the GTK engine, which determines what options you have for the theme. Ubuntu's Human theme uses Ubuntulooks, which is a variant of the popular Clearlooks engine. There's also the icon theme. I don't really know how those work. I know that Ubuntu uses "Human" icons when available, and default GNOME icons when not.

Anyway, it might be a good idea to edit an existing theme, just to give you a template to work from... you could take an existing one and change everything, stuff like that. That's how I started, during my brief foray... I copied the Human theme from "/usr/share/themes/Human" to "~/.themes/Human-Tina" and renamed it "Human-Tina," and played around with various options to see what they did. (In order to rename a theme, you have to edit its "desktop" file. This is in the theme's root folder and looks like a text file with no filename extension, but you'll need to drag it into a text editor window if you want to edit it, blagh.)

Basically, the theme structure and syntax is so weird, it might help to use an existing theme to start with, even if you decide to change everything about it, mwa ha ha.

Here are articles that I found using Google:

[http://live.gnome.org/GnomeArt/Tutorials/GtkThemes](http://live.gnome.org/GnomeArt/Tutorials/GtkThemes)
[http://developer.gnome.org/doc/tutorials/metacity/metacity-themes.html](http://developer.gnome.org/doc/tutorials/metacity/metacity-themes.html)
[http://freshmeat.net/articles/view/465/](http://freshmeat.net/articles/view/465/)

That's the end of my knowledge on this subject. I hope this helps! Good luck!

---

### Post by eyeonus on 2011-09-09
Dude. He said Emerald theme, not metacity theme.

Gtk themes and Emerald themes are /not/ the same.

---

