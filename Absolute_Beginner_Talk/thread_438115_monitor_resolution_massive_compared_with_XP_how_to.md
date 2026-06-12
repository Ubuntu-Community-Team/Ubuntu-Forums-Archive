---
title: "monitor resolution massive compared with XP? how to make everything smaller?"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by snuffy on 2007-05-09
I am running 7.04 with the resolution set at 1280 x 1024.  this is the same resolution as on my dual boot XP partition. however, everything is massive!  i am losing serious screen real estate.  icons are massive, window edges are massive, menus are massive, buttons are massive... for example in firefox i have a full line of quicklinks to websites that fit the screen.  when i open firefox in ubuntu, three of these don't fit the width.

there is no higher resolution to choose in system > prefs > screen resolution.

how do i make everything smaller?


I have a 19 inch samsung syncmaster 913n monitor, if that makes a difference.

---

### Post by jerrylamos on 2007-05-09
There are a couple of controls I know of.  Try
Ctrl-+ 
and
Ctrl - 
you have to wait a little while for them to take effect.  I actually don't use them.

Also, a number of people do:

System, Preferences, Font, Details

At the top is a resolution number.  Sometimes it defaults to 96, some people use 85 or 75.  Try them out.  Yes, I know that's a Ubuntu preference menu, but it directly affects Firefox.  I prefer 96.

Cheers, Jerry:)

---

### Post by starcraft.man on 2007-05-09
Thats not an error with Ubuntu, its designed that way. Yes, the Icons are somewhat bigger in Ubuntu, the emphasis I think has always been in using the menus and the panel at the top for launchers you use often. I only ever use the desktop for downloads, mounted drives and my wallpaper folder.

If you really must get it to look different, it is an easy fix. You can use the commands above, or change themes/skins [gnomelook]("http://www.gnome-look.org/") check for an icon set thats smaller/works for you, you can also look for a GTK theme, those are packaged bundles of fonts, window themese, menu/panel themes. If you download fonts and other things seperate you'll have to install them manually. Try a few different sets.

Most themes are installed via System > Preferences > Themes

Have fun!

---

### Post by NilsE on 2007-05-09
It sounds like it is saying that it is at 1280x1024 but it may not really be.

Go into a terminal and run:

sudo dpkg-reconfigure -phigh xserver-xorg

Select the correct display adapter when asked and then select the native resolution of the monitor when asked.  If this does not solve the problem or even makes it worse there will be a backup of the xorg.conf file in the /etc/X11/ folder with a date in the name that you can copy back if necessary.

Either before or after doing this also make sure you have a normal theme selected in Preferences/Themes since you may accidentally have large one selected.

---

