---
title: "Ubuntu studio question"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by ITdrummer on 2007-07-06
I like the way Ubuntu studio looks and i have a fairly large music collection that i like listening to very often.  How do i install Ubuntu studio.  Is it just a desktop environment or will i have to completely reinstall a new OS?

---

### Post by moredhel on 2007-07-06
it's basically another flavour of ubuntu. It's gnome, but with a new default skin (i will look for it for you know...)

The only reason to use it would be if you do music creating / editing AFAIK

EDIT:

sudo su -c 'echo deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main >> /etc/apt/sources.list'
wget -q [http://archive.ubuntustudio.org/ubuntustudio.gpg](http://archive.ubuntustudio.org/ubuntustudio.gpg) -O- | sudo apt-key add - && sudo apt-get update

:D

it has the packages:

ardour - Digital audio workstation (graphical gtk2 interface) (This is Ardour 2)
ardour-i686 - Digital audio workstation (graphical gtk2 interface) [i686] (This is Ardour 2)
ubuntustudio-desktop - Makes up our base desktop install.
ubuntustudio-audio - Ubuntu Studio audio package
ubuntustudio-audio-plugins - Ubuntu Studio audio plugins package
ubuntustudio-graphics - Ubuntu Studio graphics package
ubuntustudio-video - Ubuntu Studio video package
ubuntustudio-artwork - UbuntuStudio themes and artwork
ubuntustudio-gdm-theme - Ubuntu Studio GDM theme
ubuntustudio-icon-theme - UbuntuStudio Icon theme
ubuntustudio-look - Ubuntustudio look (metapackage)
ubuntustudio-session-splashes - Ubuntu Studio Session splashes
ubuntustudio-sounds - Ubuntu Studio's GNOME audio theme
ubuntustudio-screensaver - Ubuntu Studio's floating logo screensaver
ubuntustudio-theme - Ubuntu Studio look - GTK and Metacity theme
ubuntustudio-wallpapers - Ubuntu Studio - Wallpapers
usplash-theme-ubuntustudio - Usplash theme for Ubuntustudio
wired - Audio creation free software for Linux

So to convert feisty to studio i think you would just install ubuntustudio-desktop :)

---

### Post by Istonian on 2007-07-06
Ubuntu Studio is for people who do a lot with sound mixing, graphics and video editing. Stuff like that.

---

