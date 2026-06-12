---
title: "A load of EASY questions"
date: 2006-08-16
forum: Absolute Beginner Talk
---

### Post by Ephemeral on 2006-08-16
HEY !
I finally got internet working, did it alone =]
Anyways, Linux Ubuntu 6.06 rox0rz, but just a few suestions :
A) I haven't googled it yet, but how do I theme the desktop ?
B) How do I install aMsn, it isn't working for me :'(
C) Will the game : Mu ([www.grudgemu.com](www.grudgemu.com)) work on Ubuntu ?
I really need to play that game =]

---

### Post by Dinerty on 2006-08-16
Theme websites:

 [http://www.gnome-look.org/](http://www.gnome-look.org/)
 [http://art.gnome.org/faq.php](http://art.gnome.org/faq.php)

Are you trying to install aMSN from the synaptic package manager or you downloading it from website?, the version in the synaptic package manager is the old one.

You could use gaim to communicate with all your msn friends.

Not sure about the game sorry

---

### Post by Ephemeral on 2006-08-16
I searched MSN Linux on Google.com
I clicked on Linux and stuff, Ubuntu, etc.
Then I am sent to a download page to download : 
amsn_0.96RC1-1.deb
When I try to run it, it says in red : 
Error: depency is not satisfiable : tcltls
Thanks for the quick response =]

---

### Post by Kobalt on 2006-08-16
If you want to install the latest version of aMsn, you should follow [this HowTo.]("http://www.ubuntuforums.org/showthread.php?t=216689")

Concerning your game question, I suggest you ask it in the Gaming area of this forum, you'll get your answer from there better than from here. 

Cheers ! :rolleyes:

---

### Post by Dinerty on 2006-08-16
If you try to load up synaptic package manager now, it should detect a broken package (Which is tcltls) and allow you to fix the package by downlaoding it

I'm still a noob myself, but this always works for me if I install a deb and dependicies are not all there

---

### Post by fakie_flip on 2006-08-16
The easy way to install aMsn for a beginner is to use the automatrix script. I think automatrix has some of its own repositories to get newer software, but I am not sure. You should also enable universe and multiverse repositories if you want to get these two packages from Synaptic. See these websites. 

[https://help.ubuntu.com/ubuntu/desktopguide/C/index.html](https://help.ubuntu.com/ubuntu/desktopguide/C/index.html)
[https://wiki.ubuntu.com/SynapticHowto](https://wiki.ubuntu.com/SynapticHowto)
[https://help.ubuntu.com/ubuntu/desktopguide/C/extra-repositories.html](https://help.ubuntu.com/ubuntu/desktopguide/C/extra-repositories.html)

```
ubuntu@ubuntu:~$ apt-cache show gnome-art gnome-themes-extras
Package: gnome-art
Priority: optional
Section: universe/gnome
Installed-Size: 200
Maintainer: Dan Korostelev <dan@ats.energo.ru>
Architecture: all
Version: 0.2-1ubuntu1
Depends: ruby (>= 1.8), ruby (<< 1.9), libglade2-ruby (>= 0.11.0), gnome-splashscreen-manager
Filename: pool/universe/g/gnome-art/gnome-art_0.2-1ubuntu1_all.deb
Size: 26992
MD5sum: 01d3fc5583b45936a969954a8a1d43b1
Description: install GNOME themes from art.gnome.org
 Gnome Art is a tool for downloading and installing GNOME themes
 from http://art.gnome.org/ website. It provides a nice theme list
 with options to preview, download and install them.
 .
 Homepage: http://www.miketech.net/gnome-art/
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

Package: gnome-themes-extras
Priority: optional
Section: universe/gnome
Installed-Size: 21456
Maintainer: Josselin Mouette <joss@debian.org>
Architecture: all
Version: 0.9.0-0ubuntu1
Replaces: gtk2-engines-galaxy, gtk2-engines-gorilla, gtk2-engines-nuvola, gtk2-engines-wasp
Depends: gtk2-engines-smooth, gtk2-engines-spherecrystal, gtk2-engines-industrial, librsvg2-common
Recommends: gtk-engines-industrial, gtk-engines-smooth
Filename: pool/universe/g/gnome-themes-extras/gnome-themes-extras_0.9.0-0ubuntu1_all.deb
Size: 5693880
MD5sum: dd07d3a6ae7138afe3fd7ae5720942ad
Description: various themes for the GNOME 2 desktop
 This package contains a few nice contributed themes for the GNOME
 desktop, including vector icons for applications and nautilus, GTK+
 themes and metacity themes.
 .
  * The Amaranth theme brings a look of shiny silver.
  * The Gorilla theme is built around Jimmac's famous yellow icons.
  * The Lush theme looks like Mandrake Linux's Galaxy theme.
  * The Nuvola theme is an adaptation of David Vignoni's "blue style
    surf" theme.
  * The SphereCrystal theme provides a blue desktop with an aquatic
    design.
  * The Wasp theme makes the GNOME desktop look like the BeOS system.
 .
 Screenshots are available at: http://librsvg.sourceforge.net/theme.php
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

ubuntu@ubuntu:~$

```

---

### Post by Ephemeral on 2006-08-16
tcltls isn't in the package manager place, also, I have gaim on Ubuntu already lol =]

---

### Post by Ephemeral on 2006-08-16
I got Gaim to work, also, what can I use to unrar .rar files ?

---

### Post by lupine_nickt on 2006-08-16
Answer's in the question - you want "unrar". The package in question is actually called "unrar-free", which is in the universe repository.

It *might* integrate with the GUI archive manager, or you might need to use the command line (just "unrar <file>"). 

xF,

...Nick

---

### Post by Ephemeral on 2006-08-16
But how do I get to that file ?
If it is on the desktop, how do I de-rar it ?

---

### Post by 3rdalbum on 2006-08-16
> **Ephemeral said:**
> But how do I get to that file ?
If it is on the desktop, how do I de-rar it ?

After you've installed the unrar-nonfree package, try opening the .rar file in Archive Manager. (uh... it's either the first or the last .rar file in the series, I forget which).

If that doesn't work, go to the terminal and type:

cd Desktop
unrar e *rarfilename*

where rarfilename is the name of the .rar file.

---

### Post by Ephemeral on 2006-08-16
Managed to use unrar thing, just need to get the game to work ^^

---

