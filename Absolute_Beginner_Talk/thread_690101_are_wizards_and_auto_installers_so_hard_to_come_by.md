---
title: "are wizards and auto installers so hard to come by?"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by eniacfoa on 2008-02-07
I was wondering why there arnt wizards and auto installers?
are they that hard to program? when is it going to be as easy to use as windows? I'm a musician, im not a programmer, i cant install things via command line...why is it so hard to make this process easy?

---

### Post by fiddledd on 2008-02-07
Most programs you install don't need the command line, you can use Add Remove from the Menu or Synaptic from System Menu, both are GUIs. Also many people here when answering posts give the command to install "apt-get install whatever", that's because they feel it is easier that way. But that doesn't mean you have to do it that way, although it may sometimes be necessary.

---

### Post by mikeyphi on 2008-02-07
> **eniacfoa said:**
> I was wondering why there arnt wizards and auto installers?
are they that hard to program? when is it going to be as easy to use as windows? I'm a musician, im not a programmer, i cant install things via command line...why is it so hard to make this process easy?

I think you'll find that most can/are installed automatically - the big problem with the exceptions is often that the software/hardware is not openly available to the Ubuntu program developers. The difficulty is well appreciated and is always being worked!! Remember the windows has been around for many, many years and that drivers etc are provided by hardware manufacturers.....that process is moving forward in the Linux community.

---

### Post by Algus on 2008-02-07
You know, one of the things that drew me to Linux was the program repositories.  I love being able to click Applications->Add/Remove Program and be given a list of programs that I can install/download.  It's even easier then going to a store, buying some software for Windows and coming home to install it.  

Linux has some scary stuff for people who aren't too tech savvy but I think that's in large part because they're having to learn something "new" from Windows.  Once you get the hang of it, it really is pretty easy to use.

---

### Post by Paqman on 2008-02-07
> **eniacfoa said:**
> when is it going to be as easy to use as windows?

If you're talking about installing/removing software then I think Synaptic or Add/Remove make it waaaaaay quicker and easier than Windows. I hate having to rummage around websites for .exe files, and i've got a ridiculous ammount of Windows software install disks cluttering up my house.

---

### Post by Tatty on 2008-02-07
> **Paqman said:**
> If you're talking about installing/removing software then I think Synaptic or Add/Remove make it waaaaaay quicker and easier than Windows. I hate having to rummage around websites for .exe files, and i've got a ridiculous ammount of Windows software install disks cluttering up my house.

+1 for this.

I always hate those moments when I want some software for windows and i realise "oh, well id better go and order it from somewhere then... i guess it should be here in a week... hopefully".

Synaptic makes things so easy.  Search, Click, Done.

Although i agree software installing can become a worrying burden when you cand find what you want in synaptic - i still have not really sussed exactly how to keep track of and maintain or remove things i have installed from other methods.

But then again, the reason I have not really sussed those things is becuase 99% of the time Synaptic gives me what I want.

Autopackage seems to be quite a nice package management system too, although the only software I have ever used that uses this is amsn.

---

### Post by ferdostar on 2008-02-07
> **eniacfoa said:**
> I was wondering why there arnt wizards and auto installers?
are they that hard to program? when is it going to be as easy to use as windows? I'm a musician, im not a programmer, i cant install things via command line...why is it so hard to make this process easy? 

In fact the reason why you have the terminal (command line) is that you don't need any particular configurations about your machine. You can run the command line on a very slow computer and have all the performance you need, cause it's not consuming any resources. You can install your distro without having any particular drivers, you'll not have any desktop maybe but... :) Your are right that is MAYBE more difficult for users, who are coming from windows to type commands, but think about that you can configure and manage your system as you want and do whatever you want. Isn't great?! :)
ps as other guys wrote you have add/remove programs and synaptic if you don't like the command line ;)

---

### Post by Paqman on 2008-02-07
> **Tatty said:**
>  i still have not really sussed exactly how to keep track of and maintain or remove things i have installed from other methods.


Have you used checkinstall? If you're ever compiling anything you can use it to create a package which you can track and even uninstall through Synaptic. It's in the repos. Just replace the "make install" step with "checkinstall"

---

### Post by Tatty on 2008-02-07
> **Paqman said:**
> Have you used checkinstall? If you're ever compiling anything you can use it to create a package which you can track and even uninstall through Synaptic. It's in the repos. Just replace the "make install" step with "checkinstall"

Oh excellent!

Thank you Paqman,  after reading your post I had a look at the documentation for checkinstall and it seems like exactly what I have always been missing :)

---

### Post by erfahren on 2008-02-07
a fresh install of Windows ... download the new Firefox, Opera, Winamp, ZoneAlarm, AVG, AbiWord, GIMP, IrfanView, Flash, Java, Quicktime, etc. etc. etc.

install (one-by-one) the new Firefox, Opera, Winamp, ZoneAlarm, AVG, AbiWord, GIMP, IrfanView, Flash, Java, Quicktime, etc. etc. etc. - sit there and click, click, click


a fresh install of Ubuntu....
```

sudo apt-get install opera audacious audacious-plugins audacious-plugins-extra streamtuner vlc sun-java6-plugin gedit msttcorefonts ttf-ubuntu-title gtkorphan blender inkscape create-resources conky linuxinfo gftp-gtk gdesklets firestarter xscreensaver-data-extra xscreensaver-gl-extra dosbox gsynaptics ffmpeg nautilus-open-terminal nautilus-image-converter nautilus-script-audio-convert nautilus-wallpaper glipper build-essential auto-apt autoconf checkinstall apt-file acroread acroread-escript acroread-plugins mozilla-acroread w32codecs realplay neverball icebreaker planetpenguin-racer planetpenguin-racer-extras supertuxkart tuxkart dopewars pipenightdreams defendguin gl-117 gnubik foobillard billard-gl gtkballs gtkpool scorched3d searchandrescue slune tdfsb tomatoes torcs widelands pipenightdreams

```
- go take a nap, grab a sandwich, egg your neighbor's house, -whatever!

---

### Post by Paqman on 2008-02-07
Tatty: No probs, it's a great little tool, for sure!

Erfahren: Exactly. I also like the way you can [creat a list of installed packages](http://ubuntuforums.org/showthread.php?t=261366) and automatically reinstall them. Reinstalling a workable Windows setup takes forever compared to that.

---

### Post by ferdostar on 2008-02-08
> **erfahren said:**
> a fresh install of Windows ... download the new Firefox, Opera, Winamp, ZoneAlarm, AVG, AbiWord, GIMP, IrfanView, Flash, Java, Quicktime, etc. etc. etc.

install (one-by-one) the new Firefox, Opera, Winamp, ZoneAlarm, AVG, AbiWord, GIMP, IrfanView, Flash, Java, Quicktime, etc. etc. etc. - sit there and click, click, click


a fresh install of Ubuntu....
```

sudo apt-get install opera audacious audacious-plugins audacious-plugins-extra streamtuner vlc sun-java6-plugin gedit msttcorefonts ttf-ubuntu-title gtkorphan blender inkscape create-resources conky linuxinfo gftp-gtk gdesklets firestarter xscreensaver-data-extra xscreensaver-gl-extra dosbox gsynaptics ffmpeg nautilus-open-terminal nautilus-image-converter nautilus-script-audio-convert nautilus-wallpaper glipper build-essential auto-apt autoconf checkinstall apt-file acroread acroread-escript acroread-plugins mozilla-acroread w32codecs realplay neverball icebreaker planetpenguin-racer planetpenguin-racer-extras supertuxkart tuxkart dopewars pipenightdreams defendguin gl-117 gnubik foobillard billard-gl gtkballs gtkpool scorched3d searchandrescue slune tdfsb tomatoes torcs widelands pipenightdreams

```
- go take a nap, grab a sandwich, egg your neighbor's house, -whatever!

:lolflag:

---

### Post by seventhc on 2008-02-08
go to [http://getdeb.net/](http://getdeb.net/) everything there self installs, sort of like... a wizard, but you don't have to keep clicking '*next, next, next, next'*

---

### Post by dark_harmonics on 2008-02-08
> **erfahren said:**
> a fresh install of Windows ... download the new Firefox, Opera, Winamp, ZoneAlarm, AVG, AbiWord, GIMP, IrfanView, Flash, Java, Quicktime, etc. etc. etc.

install (one-by-one) the new Firefox, Opera, Winamp, ZoneAlarm, AVG, AbiWord, GIMP, IrfanView, Flash, Java, Quicktime, etc. etc. etc. - sit there and click, click, click


a fresh install of Ubuntu....
```

sudo apt-get install opera audacious audacious-plugins audacious-plugins-extra streamtuner vlc sun-java6-plugin gedit msttcorefonts ttf-ubuntu-title gtkorphan blender inkscape create-resources conky linuxinfo gftp-gtk gdesklets firestarter xscreensaver-data-extra xscreensaver-gl-extra dosbox gsynaptics ffmpeg nautilus-open-terminal nautilus-image-converter nautilus-script-audio-convert nautilus-wallpaper glipper build-essential auto-apt autoconf checkinstall apt-file acroread acroread-escript acroread-plugins mozilla-acroread w32codecs realplay neverball icebreaker planetpenguin-racer planetpenguin-racer-extras supertuxkart tuxkart dopewars pipenightdreams defendguin gl-117 gnubik foobillard billard-gl gtkballs gtkpool scorched3d searchandrescue slune tdfsb tomatoes torcs widelands pipenightdreams

```
- go take a nap, grab a sandwich, egg your neighbor's house, -whatever!

What an awesome list of initial programs! Some of those you might incorporate together with the ubuntu-restricted-extras and you might wanna add cool stuff like windows mapping support smbfs samba and the compizconfig-settings-manager and startupmanager packages. I love nautilus-open-terminal btw.

---

### Post by hyper_ch on 2008-02-08
you can even go further and expand that one line to a more extensive script.

```

#!/bin/bash

################ RESTORE SOURCES.LIST ###############

cp -f backup_files/sources.list /etc/apt/sources.list
cp -f backup_files/secring.gpg /etc/apt/secring.gpg
cp -f backup_files/trustdb.gpg /etc/apt/trustdb.gpg
cp -f backup_files/trusted.gpg /etc/apt/trusted.gpg

#####################################################

aptitude -y remove mozilla-thunderbird

aptitude update
aptitude -y upgrade

# Skype
aptitude -y install skype

# Java
aptitude -y install sun-java6-jre sun-java5-jre

# Postfix
aptitude -y install postfix


#KDE Appz
aptitude -y install kopete konversation konqueror k3b amarok krfb ktorrent
aptitude -y install kftpgrabber kate kontact kdepim-kio-plugins kgpg
aptitude -y install akregator gdb

# Burn Programs
aptitude -y install gnomebaker

# GnuPGP Key Management
aptitude -y install seahorse file-roller

# aMSN
aptitude -y install amsn

# IRSSI / OpenSSH
aptitude -y install irssi openssh-server

# GnuMP3d
# aptitude -y install gnump3d

# OTR
aptitude -y install python-glade-1.2 python-gtk-1.2

# VmWare
aptitude -y install linux-headers-`uname -r` build-essential xinetd

# Browsers
aptitude -y install kazehakase opera flashplugin-nonfree

# Codecs
aptitude -y install libdvdcss2 gstreamer0.10-ffmpeg gstreamer0.10-pitfdll gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui w32codecs mplayer

# VLC
aptitude -y install vlc

# Samba
aptitude -y install samba

# Midnight Commander
aptitude -y install mc

# UNRAR
aptitude -y install unrar

# GParted
aptitude -y install gparted

# CheckRootKit
aptitude -y install chkrootkit

# OpenOffice
aptitude -y install openoffice.org openoffice.org-gtk

# ImageMagic
aptitude -y install imagemagick

# Numlock & fonts
aptitude -y install numlockx msttcorefonts

# Timeserver
aptitude -y install ntp ntpdate

# HDD Encryption
aptitude -y install cryptsetup hashalot

# various
aptitude -y install whois phpmyadmin mysql-server mysql-client libmysqlclient15-dev adesklets d4x googleearth htop traceroute libjack0.100.0-dev

#######################
#######################

# Restore other files

cp -f backup_files/sysinfo /usr/share/apps/konversation/scripts/sysinfo
cp -f backup_files/screenshot /usr/bin/screenshot

```

first I replace the default sources.list and gpg-keys with a trusted copy. Then I remove the stuff I don't want... finally I install the stuff I want. I have put on top the packages that require some user interaction (that could also be automated I think).

Finally just copy back configuration files or other stuff...

---

