---
title: "Re installing Synaptic"
date: 2006-05-14
forum: Absolute Beginner Talk
---

### Post by KeyboardJockey on 2006-05-14
I'm having problems with Synaptic.  I can't quit it unless I 'force quit' which means I lose unsaved changes but I can't identfy what the changes are so I'm thinking if I start from scratch and re install Synaptic then the problems that it is having (which are probably of my doing) its telling me I've got 'five broken packages' on the system but Fix Broken doesn't appear to do anything.

Where am I going wrong and also is it possible to re install breezy without affecting my data files?

When I click OK on the broken packages dialogue box I get the following message

W: Couldn't stat source package list [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Packages (/var/lib/apt/lists/koti.mbnet.fi_%7eots_ubuntu_breezy_Packages) - stat (2 No such file or directory)

I selected the broken package filter and clicked OK an dthen went to fix broken packages.

I then clicked Apply and got the following error message:

E: /var/cache/apt/archives/libgtk2.0-common_2.8.6-0ubuntu2.1_all.deb: unable to stat `./usr/share/locale/zh_CN/LC_MESSAGES' (which I was about to install)
E: /var/cache/apt/archives/libgtk2.0-bin_2.8.6-0ubuntu2.1_i386.deb: unable to stat `./usr/share/man/fr' (which I was about to install)
E: /var/cache/apt/archives/firefox_1.0.8-0ubuntu5.10_i386.deb: unable to stat `./usr/share/pixmaps' (which I was about to install)
E: /var/cache/apt/archives/libvte-common_1%3a0.11.15-0ubuntu3_all.deb: unable to stat `./usr/share/locale/zh_CN/LC_MESSAGES' (which I was about to install)
E: /var/cache/apt/archives/totem-gstreamer_1.2.1-0ubuntu1~breezy1_i386.deb: unable to stat `./usr/share/pixmaps' (which I was about to install)
E: /var/cache/apt/archives/xchat_2.6.0-0ubuntu1~breezy1_i386.deb: unable to stat `./usr/share/pixmaps' (which I was about to install)

The errors both before I tried Automatix and now all seem to have the same element the 

E: /var/cache/apt/archives/*filename*

... and also this one...

E: /var/cache/apt/archives/libvte-common_1%3a0.11.15-0ubuntu3_all.deb: unable to stat `./usr/share/locale/zh_CN/LC_MESSAGES' (which I was about to install)
E: /var/cache/apt/archives/totem-gstreamer_1.2.1-0ubuntu1~breezy1_i386.deb: unable to stat `./usr/share/pixmaps' (which I was about to install)

Any ideas?  Because I'm lost and beginning to look wistfully at my copy of winXP ](*,)

---

### Post by Sef on 2006-05-14
> Where am I going wrong and also is it possible to re install breezy without affecting my data files?


If you have a home partition, it is possible to reinstall Breezy and leave your data intact.  However, do a **back up**.   sometimes things go wrong.  

This line > /var/lib/apt/lists/koti.mbnet.fi_%7eots_ubuntu_breezy_Packages

is the source of your problems.   However, I am not sure the best way to either delete or comment it.  (Commenting it would tell the os to ignore it.)

Hmm...to comment it Open the terminal (applications > accessories > terminal)

then

sudo gedit /etc/apt/source.list  

If you see that line then put a # before it.

---

### Post by gingermark on 2006-05-14
it's "/etc/apt/source**s**.list".

---

### Post by KeyboardJockey on 2006-05-14
[QUOTE=Sef]If you have a home partition, it is possible to reinstall Breezy and leave your data intact.  However, do a **back up**.   sometimes things go wrong.  

This line 

is the source of your problems.   However, I am not sure the best way to either delete or comment it.  (Commenting it would tell the os to ignore it.)

Hmm...to comment it Open the terminal (applications > accessories > terminal)

then

sudo gedit /etc/apt/source.list  

If you see that line then put a # before it.[/QUOTE]


Tried this sudo gedit /etc/apt/sources.list    gave me the following:

deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
## deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe main restricted multiverse

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) breezy main
deb-src [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) breezy main

deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free

deb [http://kubuntu.org/packages/kde351](http://kubuntu.org/packages/kde351) breezy main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://koti.mbnet.fi/~ots/ubuntu/](http://koti.mbnet.fi/~ots/ubuntu/) breezy/
deb-src [http://koti.mbnet.fi/~ots/ubuntu/](http://koti.mbnet.fi/~ots/ubuntu/) breezy/

## created by arnielistenremoved


The Terminal window gave me:

 sudo gedit /etc/apt/sources.list
Password:

** (gedit:10264): CRITICAL **: failed to load icon: /usr/share/pixmaps/lpi-help.png

** (gedit:10264): CRITICAL **: failed to load icon: /usr/share/pixmaps/lpi-translate.png



Confused??

no sign of the offending code line at all.

And now just to cap it all can't paste into the Terminal Window.

---

