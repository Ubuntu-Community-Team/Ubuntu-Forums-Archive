---
title: "How do I install ubuntu studio in ubuntu 7.04?"
date: 2007-09-27
forum: Art &amp; Design
---

### Post by suchawato on 2007-09-27
I have 7.04 already running.
I added the ubuntustudio repositories using the instructions on the ubuntustudio website.
I am an art student and I will probbably find some of the features very usefull (such as wacom art tablet utils.)
I attempted:
[COLOR="DarkOrchid"]sudo aptitude update && sudo aptitude install ubuntustudio-desktop[/COLOR]
however I was prompted with several conficts with existing files already installed, and "suggested solutions".
I thought I'd post and see if anyone knows how to do it properly.
Thanks in advance, 
-Stu

---

### Post by mrrobbit on 2007-09-28
Hi,

You can either visit [www.ubuntustudio.org/downloads](www.ubuntustudio.org/downloads) or enter the commands below:

sudo su -c 'echo deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main >> /etc/apt/sources.list'
wget -q [http://archive.ubuntustudio.org/ubuntustudio.gpg](http://archive.ubuntustudio.org/ubuntustudio.gpg) -O- | sudo apt-key add - && sudo apt-get update

Packages in our repo:

    * ardour - Digital audio workstation (graphical gtk2 interface) (This is Ardour 2)
    * ardour-i686 - Digital audio workstation (graphical gtk2 interface) [i686] (This is Ardour 2)
    * ubuntustudio-desktop - Makes up our base desktop install.
    * ubuntustudio-audio - Ubuntu Studio audio package
    * ubuntustudio-audio-plugins - Ubuntu Studio audio plugins package
    * ubuntustudio-graphics - Ubuntu Studio graphics package
    * ubuntustudio-video - Ubuntu Studio video package
    * ubuntustudio-artwork - UbuntuStudio themes and artwork
    * ubuntustudio-gdm-theme - Ubuntu Studio GDM theme
    * ubuntustudio-icon-theme - UbuntuStudio Icon theme
    * ubuntustudio-look - Ubuntustudio look (metapackage)
    * ubuntustudio-session-splashes - Ubuntu Studio Session splashes
    * ubuntustudio-sounds - Ubuntu Studio's GNOME audio theme
    * ubuntustudio-screensaver - Ubuntu Studio's floating logo screensaver
    * ubuntustudio-theme - Ubuntu Studio look - GTK and Metacity theme
    * ubuntustudio-wallpapers - Ubuntu Studio - Wallpapers
    * usplash-theme-ubuntustudio - Usplash theme for Ubuntustudio
    * wired - Audio creation free software for Linux

---

### Post by Elotero on 2007-10-05
Enter this in the terminal too? or is it just stating whats packagaed? 
Packages in our repo:

* ardour - Digital audio workstation (graphical gtk2 interface) (This is Ardour 2)
* ardour-i686 - Digital audio workstation (graphical gtk2 interface) [i686] (This is Ardour 2)
* ubuntustudio-desktop - Makes up our base desktop install.
* ubuntustudio-audio - Ubuntu Studio audio package
* ubuntustudio-audio-plugins - Ubuntu Studio audio plugins package
* ubuntustudio-graphics - Ubuntu Studio graphics package
* ubuntustudio-video - Ubuntu Studio video package
* ubuntustudio-artwork - UbuntuStudio themes and artwork
* ubuntustudio-gdm-theme - Ubuntu Studio GDM theme
* ubuntustudio-icon-theme - UbuntuStudio Icon theme
* ubuntustudio-look - Ubuntustudio look (metapackage)
* ubuntustudio-session-splashes - Ubuntu Studio Session splashes
* ubuntustudio-sounds - Ubuntu Studio's GNOME audio theme
* ubuntustudio-screensaver - Ubuntu Studio's floating logo screensaver
* ubuntustudio-theme - Ubuntu Studio look - GTK and Metacity theme
* ubuntustudio-wallpapers - Ubuntu Studio - Wallpapers
* usplash-theme-ubuntustudio - Usplash theme for Ubuntustudio
* wired - Audio creation free software for Linux

---

### Post by argraff on 2007-10-12
Those are what's included. Let me know how you like it - I've been considering it myself!

---

### Post by suchawato on 2007-10-13
I suppose I should just apt-get all of these?
I wonder if there is an easier way to do that than just one at a time...
Oh well, I will try this and get back to you. 
Thanks.

---

### Post by suchawato on 2007-10-13
Actually, will all of these install on their own?
Or do I have to run an aptitude install command on each or some of these?

---

### Post by argraff on 2007-10-13
[QUOTE=mrrobbit;3439143]

sudo su -c 'echo deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main >> /etc/apt/sources.list'
wget -q [http://archive.ubuntustudio.org/ubuntustudio.gpg](http://archive.ubuntustudio.org/ubuntustudio.gpg) -O- | sudo apt-key add - && sudo apt-get update

It's only two lines - I would do it in the terminal. If you do this, all of the other stuff will magically exist on your harddrive!

---

### Post by Stretsh on 2007-10-13
> **suchawato said:**
> Actually, will all of these install on their own?
Or do I have to run an aptitude install command on each or some of these?

[https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromFeisty](https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromFeisty) has the details.

---

### Post by suchawato on 2007-10-22
I actually just upgraded to Gutsy, and I havn't been able to find the repositories list for the gutsy version yet .
Does anyone know how do to the same request with gutsy?
I tried editing the fiesty  install to use the words "gutsy" instead of fiesty, but that didn't work, The package manager didn't recognize it as a valid source

---

### Post by colllin on 2007-10-22
> **suchawato said:**
> I actually just upgraded to Gutsy, and I havn't been able to find the repositories list for the gutsy version yet .
Does anyone know how do to the same request with gutsy?
I tried editing the fiesty  install to use the words "gutsy" instead of fiesty, but that didn't work, The package manager didn't recognize it as a valid source

It seems that the ubuntu studio packages are included in the ubuntu universe repositories. 

This should work:
```
sudo aptitude install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video
```

---

### Post by suchawato on 2007-10-23
well, it installed mostly correctly.
mostly.
what didn't install correctly was the new bootline in grub.
it will boot, but will not load the network, or the themes daemon,
If I just boot to the previous generic line, and load the themes in the login window and appearance themes windows, it appears to be fully functional. 
all applications seemed to install correctly as far as I can tell.
Question:
which bit is part of the wacom utils for art tablets?
do I just plug it in now and it will auto-detect, or do I have to launch some proogram to get it running?
Thanks  in advance,
Stu

---

