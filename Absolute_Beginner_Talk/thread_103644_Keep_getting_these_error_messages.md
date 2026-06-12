---
title: "Keep getting these error messages"
date: 2005-12-14
forum: Absolute Beginner Talk
---

### Post by Kreat on 2005-12-14
> Errors were encountered while processing:
 emacs21
 cedet-common
 eieio
 speedbar
E: Sub-process /usr/bin/dpkg returned an error code (1)


i tried installing them from synaptic package manager and didnt install properly.  Any way to fix this?

---

### Post by endersshadow on 2005-12-14
A couple of things:

1. Open up your terminal (Applications>Accessories>Terminal) and do the following commands:

```
sudo apt-get update
sudo apt-get install emacs21 cedet-common eieio speedbar
```

If there's an error code from that, post it here.  Also, go to #2

2. Run this command in the terminal:

```
sudo gedit /etc/apt/sources.list
```

Copy and paste what pops up into here.

Thanks!

---

### Post by Kreat on 2005-12-14
[QUOTE=endersshadow]A couple of things:

1. Open up your terminal (Applications>Accessories>Terminal) and do the following commands:

```
sudo apt-get update
sudo apt-get install emacs21 cedet-common eieio speedbar
```

Error loading speedbar... ignored.
Wrote /usr/share/emacs21/site-lisp/eieio/eieio-opt.elc
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/eieio/eieio-speedbar.el:
  !! Wrong type argument ((stringp nil))
Done
emacs-install: /usr/lib/emacsen-common/packages/install/eieio emacs21 failed at /usr/lib/emacsen-common/emacs-install line 28, <TSORT> line 5.
dpkg: error processing emacs21 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of cedet-common:
 cedet-common depends on emacs21 | emacsen; however:
  Package emacs21 is not configured yet.
  Package emacsen is not installed.
  Package emacs21 which provides emacsen is not configured yet.
dpkg: error processing cedet-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of eieio:
 eieio depends on emacs21 | emacsen; however:
  Package emacs21 is not configured yet.
  Package emacsen is not installed.
  Package emacs21 which provides emacsen is not configured yet.
dpkg: error processing eieio (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of speedbar:
 speedbar depends on cedet-common; however:
  Package cedet-common is not configured yet.
dpkg: error processing speedbar (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 emacs21
 cedet-common
 eieio
 speedbar
E: Sub-process /usr/bin/dpkg returned an error code (1)

If there's an error code from that, post it here.  Also, go to #2

2. Run this command in the terminal:

```
sudo gedit /etc/apt/sources.list
```

Copy and paste what pops up into here.

Thanks![/QUOTE]

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

deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

deb [http://public.planetmirror.com/pub/plf/ubuntu/plf/](http://public.planetmirror.com/pub/plf/ubuntu/plf/) breezy free non-free

deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free
deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free

deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free
## deb [http://seveas.ubuntulinux.nl/](http://seveas.ubuntulinux.nl/) breezy-seveas breezy-backports breezy-custom breezy-extras freenx madwifi
## deb-src [http://seveas.ubuntulinux.nl/](http://seveas.ubuntulinux.nl/) breezy-seveas breezy-backports breezy-custom breezy-extras freenx madwifi

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras main restricted universe multiverse
## created by arniebackports


----------------------------------------
thanks i appreciate the help guys,  looks like i still got it

---

### Post by endersshadow on 2005-12-14
Are you getting these errors whenever you try to install anything else via Synaptic?

And I see that you used Automatix.  Care to post your automatix.log from your Home folder, too?

---

### Post by Kreat on 2005-12-14
I get it when i try to install in the terminal and synaptic

heres the autmatix log (ithink)
> #!/bin/bash
# Automatix is copyrighted by arnieboy
# Automatix is released under the General Public License Please refer to GPL.txt)
# Written by arnieboy.
# Credit goes to keyes for showing the way.

zenity --info --title "Automatix" --text \
$"Contributors:

Written by arnieboy
Automatix is copyright / trademarked by arnieboy
Automatix is released under the General Public license (Please refer to gpl.txt)
Credit goes to keyes for showing the way
Icon Created by edm00se
This work is mostly a compilation of HowTos from ubuntuforums and ubuntuguide. 
Thanks to everyone who has indirectly contributed to this effort."
zenity --info --title "Automatix" --text $"Please NOTE that downloading and installing w32codecs, libdvdcss2 and other non-free codecs without paying a fee to the concerned authorities constitutes a CRIME in the United State of America. Hence if you are viewing this message from anywhere in the United States of America, please do not install option AUD-DVD codecs. If you are not from the United States of America, and take full responsibility for the legal consequences of downloading and installing the afore-mentioned codecs, then you can go ahead and install the same. Under any circumstances, the maker of Automatix is NOT responsible for your actions which includes and is NOT restricted to downloading and installing these codecs";
if cat /etc/apt/sources.list | grep "hoary-security";
then zenity --info --title "Automatix" --text $"This is a Breezy version of automatix. It wont work on Hoary";
exit 1;
elif cat /etc/apt/sources.list | grep "dapper-security";
then zenity --info --title "Automatix" --text $"This is a Breezy version of automatix. It wont work on Dapper"; 
exit 1;
elif cat /etc/apt/sources.list | grep "warty-security";
then zenity --info --title "Automatix" --text $"This is a Breezy version of automatix. It wont work on Warty"; 
fi
if ! cat $HOME/automatix.log | grep "Wine"; 
then zenity --info --title "Automatix" --text $"If you choose to install wine, please run 'winecfg' to configure wine after automatix exits!";
fi
if ! test -e $HOME/automatix.log;
	then
	zenity --info --title "Automatix" --text $"Please enter a ROOT password of your choice when 'Enter new Unix password' is displayed";
	gnome-terminal --command="sudo passwd root" 
	gnome-terminal --command="/usr/local/automatix/autoscript"
	else
	gnome-terminal --command="/usr/local/automatix/autoscript"
fi
	



---

### Post by arnieboy on 2005-12-16
The only package that has a problem here is **emacs21** (the other packages depend on **emacs21** and since it is not configured correctly, the others are not getting installed.)
For some reason, apt broke your **emacs21** package. you need to remove it completely from system and cache and then reinstall it to correct this problem.
These things happen occasionally with apt repos when there is a sudden interruption in an apt installation or some package in the repos gets borked.. but there are ways to correct them.

---

