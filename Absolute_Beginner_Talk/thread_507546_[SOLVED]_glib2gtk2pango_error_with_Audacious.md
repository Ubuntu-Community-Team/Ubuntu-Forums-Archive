---
title: "[SOLVED] glib2/gtk2/pango error with Audacious"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by funkshun on 2007-07-23
Trying to install Audacious. I save the file into my home folder. Then i "cd" into the audacious folder. I then "./configure" it starts to check for feature and then this error comes up.

checking for ranlib... /usr/bin/ranlib
checking for audacious... no
checking for pkg-config... /usr/bin/pkg-config
[B]checking for glib-2.0 >= 2.6.0 gtk+-2.0 >= 2.6.0 gthread-2.0 pango... no
configure: error: Cannot find glib2/gtk2/pango[/B]
funkshun@funkshun-laptop:~/audacious-1.3.2$

I tried to use synaptic and it could not find the program. Hence me trying it manualy.
Any help would be most appriciated. Thanks

---

### Post by Mornedhel on 2007-07-23
packages.ubuntu.org returns a package named "audacious" for Feisty.

Did you enable the Universe repository ?

---

### Post by funkshun on 2007-07-23
No, how do I do that? Noob here...just installed ubuntu yesterday. Thanks

---

### Post by Mornedhel on 2007-07-23
The less GUI-esque way is to edit your sources list (OK, so you'll have to play with the console a bit, but really not much, and that way you can learn).

On a terminal type :
sudo gedit /etc/apt/sources.list

Find the lines where your sources are :
deb [http://some-url-here.com/](http://some-url-here.com/) feisty main restricted (or something that looks like it)
and replace it with :
deb [http://some-url-here.com/](http://some-url-here.com/) feisty main restricted universe multiverse

Same goes for feisty-updates, feisty-backports and feisty-security. Now save the file and exit gedit. Now type :
sudo apt-get update

And the package count will suddenly increase. Audacious is in the Universe section, you can now get it via Synaptic, Adept, aptitude, apt-get, Add/Remove or your software of choice.

You may want to enable third-party repositories as well (Medibuntu for commercial DVD reading, .wmv playback, and more not-completely-legal-in-the-US stuff).

Edit : Oh, just in case you don't know yet, apt-get and brothers will take care of any dependencies, so if you ask for Audacious, pango and the other stuff it needs will automatically be selected for installation, and when you click Apply, they will be downloaded and set up as well.

---

### Post by funkshun on 2007-07-23
I tried this and synaptics still does not recognize audacious.

This is my sources.list after I did those reconmendations.


deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

Does this look ok? Any help would be appriciated thanks.

---

### Post by funkshun on 2007-07-23
I figured it out. I went to the audacious website. I then added this code to my 
I then typed in my console$:   sudo gedit /etc/apt/sources.list
and added this code

deb [http://static.audacious-media-player.org/ubuntu](http://static.audacious-media-player.org/ubuntu) dapper main
deb-src [http://static.audacious-media-player.org/ubuntu](http://static.audacious-media-player.org/ubuntu) dapper main

then I typed in terminal " sudo apt-get update " and then I went to add/remove a file and was able to install the program.  :guitar:

---

