---
title: "Zukitwo GTK3, GTK2 and GNOME-Shell theme."
date: 2011-05-25
forum: Art &amp; Design
---

### Post by LarsKongo on 2011-05-25
[CENTER][IMG]http://data.fuskbugg.se/skalman02/4ddd1a478e7ec_desk-preview.png[/IMG][/CENTER]

**Download Mirror 1:** [http://lassekongo83.deviantart.com/art/Zukitwo-203936861](http://lassekongo83.deviantart.com/art/Zukitwo-203936861)
**Download Mirror 2:** [http://gnome-look.org/content/show.php?content=140562](http://gnome-look.org/content/show.php?content=140562)

My first major theme for GTK-3.0 and GNOME-Shell. (But you can also use the GTK-2.0 theme in Gnome 2.32.) I'm trying to make it as consistent as possible. The GTK-2.0 theme still looks better than the GTK-3.0 theme, but that's because of limitations in the GTK3 CSS engine. I'm not sure if I want to make the gtk-2.0 style look as flat as the gtk3 style. I'm hoping for a gtk3 update with box-shadow support. ;)

If you notice any bugs, please post them here. :)

**Known bugs:**
- In Ubuntu 11.04 classic mode. The right-click menu on some panel applets have a white text and uses the pixmap hover effect. This only happens in Ubuntu 11.04.
- Older versions of Libreoffice have a missing scrollbar. Upgrading to Libreoffice 3.4 fixes this.

> [SIZE="1"]############################
#      HOW TO INSTALL      #
############################

To use this theme you'll need the LATEST stable versions of the following software:

- Gnome 2.32 or Gnome 3.
- The Murrine GTK2 engine 0.98.1.1 or later. (Package name varies between distributions. This engine should be installed by default in Ubuntu.)
- The Pixbuf GTK2 engine (Package name varies between distributions. This engine should be installed by default in Ubuntu.)
- Nautilus-Elementary (Not needed. But it's recommended.)
- gnome-tweak-tool (If you're using Gnome 3.)

## INSTALLING THE GTK2 THEME ##

Unzip the included folder(s) to 1 of the following locations:
/usr/share/themes
/home/your username/.themes

Go to System -> Preferences -> Appearance and click on the Customize button.
Select the theme(s) from the lists there.

Note: The /.themes folder is only for your user. If you for example open Synaptic or any other administrative application it will not be styled.

## INSTALLING THE GTK3 & GNOME-SHELL THEME ##

Unzip the included folder(s) to 1 of the following locations:
/usr/share/themes
/home/your username/.themes

Note: The /.themes folder is only for your user. If you for example use an application as root, it will not be styled.

Go to System -> Accessories -> Advanced Settings (Well, it's called something like that in English. My menu entry is in Swedish.)
In this app (gnome-tweak-tool) you can select the GTK theme and metacity theme.

To use the GNOME-Shell theme you need to install gnome-shell-extensions-common and gnome-shell-extension-user-theme/Theme Selector.
These packages may not be available in your distribution's repository.
More info here: [http://www.webupd8.org/2011/04/themeselector-gnome-shell-extension-to.html](http://www.webupd8.org/2011/04/themeselector-gnome-shell-extension-to.html)

## USING A TRANSPARENT PANEL BACKGROUND ##

1. Right-click on your panel and select properties. 
2. Set the height to 32px and the position to bottom. 
3. Click on the Background tab and select to use a custom background image.
4. Select the panelbg.png file from this theme. (home/your username/.themes/Zukitwo/panelbg.png)
If the panel didn't become transparent you're using an old version of Gnome, or you are not using the Zukitwo GTK theme.

## USING A CUSTOM PANEL BACKGROUND IN GNOME 3 FALLBACK MODE (RECOMMENDED) ##

1. ALT + Right-click on your panel and select properties. 
2. Click on the Background tab and select to use a custom background image.
3. Select the panelbg.png file from this theme. (home/your username/.themes/Zukitwo/panelbg.png)[/SIZE]

---

### Post by bmbaker on 2011-05-25
super dude ;-) 
I just shared it with Andrew at webupd8 :-)

---

### Post by nilarimogard on 2011-05-26
@bmbaker: so this is the theme? Your link in the comment was wrong :D

@LarsKongo: really really nice work!

---

### Post by bmbaker on 2011-05-26
> **nilarimogard said:**
> @bmbaker: so this is the theme? Your link in the comment was wrong :D

@LarsKongo: really really nice work!

really! i just copied it from above !!!
should have copied the link location ...... sorry !!

---

### Post by Roasted on 2011-06-08
Very nice theme my friend. I found this earlier and installed it on all of my Ubuntu machines. I enjoy it very much.

I did make some CSS alterations, though. I liked the "Darkest" theme but the thing I had trouble with was the white text. Granted, I know it's difficult to make text readable when the background colors are getting darker and darker. So (hope you won't take offense to me making my own changes to your already awesome theme) I made some changes to them. 

I'm using the dark blue highlight color as well as the window border of the "Darkest" theme, along with the main "Dark" theme as the core. I edited the sidemenu color in "Dark" to make it feel more like the "Darkest" theme. Likewise, I made all of the text nearly jet black. I felt it was a little too light of gray for me to really see sharply when using the theme on my work system.

It ended up turning out very nice, and I'm extremely happy with everything about this theme. Perhaps you could help me with something though. There are certain times I get a dialog box up with buttons on the screen. These buttons are blue, but they are very light blue. Where in the css file are these at so I can edit them to be darker blue?

But hey, solid theme. Hands down the best one on Gnome-Look right now, easily.

EDIT - I see in your "copying" file that you do not permit changing. Is this in regard to changing the theme, or changing the license? Later it specified about modifying the file so I got confused in regard to that. Is it okay for me to change this theme or was it referring to the GPL license?

---

### Post by LarsKongo on 2011-06-09
> **Roasted said:**
> Perhaps you could help me with something though. There are certain times I get a dialog box up with buttons on the screen. These buttons are blue, but they are very light blue. Where in the css file are these at so I can edit them to be darker blue?

But hey, solid theme. Hands down the best one on Gnome-Look right now, easily.

EDIT - I see in your "copying" file that you do not permit changing. Is this in regard to changing the theme, or changing the license? Later it specified about modifying the file so I got confused in regard to that. Is it okay for me to change this theme or was it referring to the GPL license?
Thanks. :)

I'm not exactly sure which buttons you mean. It could be a gtk2 application though. Open the gtkrc file in the gtk-2.0 folder and change selected_bg_color to a darker blue color.

It's just the copying file that's not allowed to be changed. The theme can be changed however you like. :)

---

### Post by Roasted on 2011-06-09
> **LarsKongo said:**
> Thanks. :)

I'm not exactly sure which buttons you mean. It could be a gtk2 application though. Open the gtkrc file in the gtk-2.0 folder and change selected_bg_color to a darker blue color.

It's just the copying file that's not allowed to be changed. The theme can be changed however you like. :)

Bingo. There it is my friend. That button color now seems to fit more since I darkened the other colors. Very nice. I figured I'd post a screen shot of my home directory to give a basic idea of what alterations I made:

[[IMG]http://img89.imageshack.us/img89/5573/screenshot1nbw.png[/IMG]](http://img89.imageshack.us/i/screenshot1nbw.png/)

Like I said, it's basically a hybrid of Dark and Darkest. I liked areas of both so much and the theme was so well rounded, so a few hex edits later and some toying with the color palette in gimp and here goes.

Thanks again dude. Solid work.

---

