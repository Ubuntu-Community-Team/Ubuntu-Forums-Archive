---
title: "Confused about GNOME themes"
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by Jadd on 2007-01-30
I'm confused about what my GNOME themes are on my ubuntu 6.06.
If I go to [www.gnome-look.org]("http://www.gnome-look.org"), I get so many different categories:

[LIST]
[*]GTK 1.x
[*]GTK 2.x
[*]Metacity
[*]Compiz
[*]Beryl
[*]Icon Themes
[*]GDM Themes
[*]Splash Screens
[*]Desklets
[*]XMMS Themes
[*]Screenshots
[*]Fonts
[*]Cliparts
[/LIST]

[art.gnome.org]("http://art.gnome.org") gives some more categories, a bit less confusing:

[LIST]
[*]Desktop Themes 
[*]Application
[*]Window Border
[*]Icons
[*]Login Manager
[*]Splash Screen
[*]GTK+ Engines
[/LIST]

What on earth are these different categories? Which ones does my ubuntu support by default?

---

### Post by kpkeerthi on 2007-01-30
GTK2.x themes change the way UI controls like buttons, checkbox etc. look
Metacity themes to change the way your window title bar looks
GDM themes change the way your login window looks
Icon themes to change your icons

.. I think the rest are pretty self explanatory

---

### Post by Jadd on 2007-01-30
Thanks for your answer, but the rest aren't self-explanatory! What's GTK 1? What are compiz, beryl and splash screens? Nowhere in the ubuntu documentation could I find that the themes were called metacity, or relied on them. (I do know what metacity is (a windows manager), but it took me quite some time to figure it out, because it's never mentionned anywhere on ubuntu dapper)

---

### Post by allthegoodnamesaretakin on 2007-01-30
I believe GTK 1.X  is an earlier version of GTK 2.X , could be wrong though.:D 
Compiz and Beryl are programs that let you do a bunch of funky stuff with your desktop environment , like view your desktops on a cube, wiggle effects, scaling windows, etc. To get a better idea of beryl just hit their website at [http://www.beryl-project.org/index.php](http://www.beryl-project.org/index.php)

Hope this helps

---

### Post by jordanmthomas on 2007-01-30
[LIST]
[*]GTK 1.x  -- old Gnome programs.  You will probably not want to use these unless you like old themes
[*]GTK 2.x  -- Gnome application controls, and your panel, etc.  These change the overall look of Gnome
[*]Metacity  --  The window borders -- title bar, min / max /close buttons, etc.
[*]Compiz  --  a composited (accelerated) window manager.  These are window borders for compiz (if you don't know what it is you don't have it installed)  ( [http://en.wikipedia.org/wiki/Compiz](http://en.wikipedia.org/wiki/Compiz) )
[*]Beryl  --  beryl is a fork of compiz and these are also window border themes.  Like compiz, this is not installed by default in Ubuntu  ( [http://beryl-project.org](http://beryl-project.org) )
[*]Icon Themes -- The icons used in GTK apps.  Look around at all your icons.  These themes will change those icons
[*]GDM Themes -- logon screen themes
[*]Splash Screens  -- Screens similar to what you get when you log in (loading panel...etc), or when you start OpenOffice  (start it and you'll see what I am talking about)
[*]Desklets  --  themes for a program called gDesklets (not sure if it installed by default in Ubuntu)
[*]XMMS Themes  -- XMMS is an old media player.  These are themes for it
[*]Screenshots  --  Screenshots people have posted (you won't be able to see them by default as screenshots are filtered at gnome-look
[*]Fonts  -- these you can install by placing them in ~/.fonts 
[*]Cliparts -- I believe these are just random little pictures you can use for various purposes
[/LIST]

[art.gnome.org]("http://art.gnome.org") gives some more categories, a bit less confusing:

[LIST]
[*]Desktop Themes -- Wallpaper
[*]Application -- GTK 2.x themes
[*]Window Border  -- metacity themes
[*]Icons -- Same as at gnome-look
[*]Login Manager  -- GDM
[*]Splash Screen -- The screen you see after logging in but before you are 100% ready to use your computer
[*]GTK+ Engines  --  some themes rely on these engines.  If you install a GTK theme that doesn't look like what you expected you will want to see if it relies on a particular engine.  If it does, you can probably get it here
[/LIST]


In case you didn't know, you generally install themes by dragging the .tar.gz on to the window that comes up if you go to System --> Preferences --> Theme
If it complains, you will have to manually extract the contents of the tarball into ~/.themes (for GTK themes and metacity) ~/.icons (for icon themes)  
Anything other than GTK, metacity, and icon themes must be installed using the appropriate program.  ie you would use XMMS to install XMMS themes

maybe this helps?

---

### Post by mostwanted on 2007-01-30
> **jordanmthomas said:**
> [LIST]
[*]GTK 1.x  -- old Gnome programs.  You will probably not want to use these unless you like old themes
[*]GTK 2.x  -- Gnome application controls, and your panel, etc.  These change the overall look of Gnome
[*]Metacity  --  The window borders -- title bar, min / max /close buttons, etc.
[*]Compiz  --  a composited (accelerated) window manager.  These are window borders for compiz (if you don't know what it is you don't have it installed)  ( [http://en.wikipedia.org/wiki/Compiz](http://en.wikipedia.org/wiki/Compiz) )
[*]Beryl  --  beryl is a fork of compiz and these are also window border themes.  Like compiz, this is not installed by default in Ubuntu  ( [http://beryl-project.org](http://beryl-project.org) )
[*]Icon Themes -- The icons used in GTK apps.  Look around at all your icons.  These themes will change those icons
[*]GDM Themes -- logon screen themes
[*]Splash Screens  -- Screens similar to what you get when you log in (loading panel...etc), or when you start OpenOffice  (start it and you'll see what I am talking about)
[*]Desklets  --  themes for a program called gDesklets (not sure if it installed by default in Ubuntu)
[*]XMMS Themes  -- XMMS is an old media player.  These are themes for it
[*]Screenshots  --  Screenshots people have posted (you won't be able to see them by default as screenshots are filtered at gnome-look
[*]Fonts  -- these you can install by placing them in ~/.fonts 
[*]Cliparts -- I believe these are just random little pictures you can use for various purposes
[/LIST]

[art.gnome.org]("http://art.gnome.org") gives some more categories, a bit less confusing:

[LIST]
[*]Desktop Themes -- Wallpaper
[*]Application -- GTK 2.x themes
[*]Window Border  -- metacity themes
[*]Icons -- Same as at gnome-look
[*]Login Manager  -- GDM
[*]Splash Screen -- The screen you see after logging in but before you are 100% ready to use your computer
[*]GTK+ Engines  --  some themes rely on these engines.  If you install a GTK theme that doesn't look like what you expected you will want to see if it relies on a particular engine.  If it does, you can probably get it here
[/LIST]


In case you didn't know, you generally install themes by dragging the .tar.gz on to the window that comes up if you go to System --> Preferences --> Theme
If it complains, you will have to manually extract the contents of the tarball into ~/.themes (for GTK themes and metacity) ~/.icons (for icon themes)  
Anything other than GTK, metacity, and icon themes must be installed using the appropriate program.  ie you would use XMMS to install XMMS themes

maybe this helps?

Nice post!

---

### Post by Waappu on 2007-01-30
Hi

Yes, nice post. Why they don't have this info on gnome-look.org ?

---

### Post by lyceum on 2007-01-30
If you want to make it really easy, sudo apt-get gnomeart (if that is wrong, got to synaptic package manager and search for "Gnome art" selcet it and install it). It gives you a box in System/Preferances called -you guessed it- Gnome art. This links to Art.gnome.org and you can pull all kinds of icons, wallpapers and more to view then install what you like. It is a very usefull tool.

---

### Post by Jadd on 2007-01-31
> **lyceum said:**
> If you want to make it really easy, sudo apt-get gnomeart (if that is wrong, got to synaptic package manager and search for "Gnome art" selcet it and install it). It gives you a box in System/Preferances called -you guessed it- Gnome art. This links to Art.gnome.org and you can pull all kinds of icons, wallpapers and more to view then install what you like. It is a very usefull tool.
Almost right, it's sudo apt-get install gnome-art actually. It's quite good, except it takes a long time to download the list of backgrounds/window borders/etc. , with no way to cancel.

Thank you so much for your reply, jordanthomas. That was _exactly_ what I was looking for. This information really should be on [www.gnome-look.org](www.gnome-look.org).

---

### Post by lyceum on 2007-01-31
> **Jadd said:**
> This information really should be on [www.gnome-look.org](www.gnome-look.org).

That is my only real complain about art.gnome.org & gnome-look.org. They **really** need a "how-to" area. I would love to see not just how to install but how to make as well.

---

### Post by ComplexNumber on 2007-01-31
> **lyceum said:**
> That is my only real complain about art.gnome.org & gnome-look.org. They **really** need a "how-to" area. I would love to see not just how to install but how to make as well.
[http://live.gnome.org/GnomeArt/Tutorials/](http://live.gnome.org/GnomeArt/Tutorials/)

---

### Post by lyceum on 2007-01-31
> **ComplexNumber said:**
> [http://live.gnome.org/GnomeArt/Tutorials/](http://live.gnome.org/GnomeArt/Tutorials/)

Awesome! Thanks!

---

### Post by ComplexNumber on 2007-01-31
it needs updating a bit in the area of theme engines. it doesn't include some of the more recent ones such as murrine and rezlooks. clearlooks is strangely left out too.

---

