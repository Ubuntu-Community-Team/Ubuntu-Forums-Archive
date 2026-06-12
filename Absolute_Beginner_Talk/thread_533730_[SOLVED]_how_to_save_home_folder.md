---
title: "[SOLVED] how to save home folder"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by DarinB on 2007-08-24
i have a system that is 160 Gb hard drive. a separate 80 Gb ntfs hard drive with my itunes music. 
how do i save my home folder to a separate usb drive and ??? maybe aptoncd iwth my apts??
so if i have to redo my system i can get it all back. 
what folders do i need to save and how do i put them back??
maybe??? a ghost type program is what i want...do we have a ghost program and just ghost my drive to an  external usb drive and have it that way.
what should i do help??
i am tired of having to redo my system.

sorry about all these newbie questions, in windows i just had a ghost of my hard drive and just put it back when i got a virus or messed it up.

thanks all
db

---

### Post by hyper_ch on 2007-08-24
Well, there are multiple approaches on how to do backups.

I prefer not to make images (like ghost) but saving the actual files. Depending on what you have done with your computer you should have all data in /home
That's the place where you normally should store your user data and where the configuration files are for all the programs you use.

So backing those up should be sufficent.

so I would do this:

(1) Format the extern drive with ext3

(2) Copy all the files there
```

sudo cp -Rp /home/* /media/usb_drive/home/

```

(3) Also backing up the sources.list
```

sudo cp -p /etc/apt/sources.list /media/usb_drive/etc/
sudo cp -p /etc/apt/secring.gpg /media/usb_drive/etc/
sudo cp -p /etc/apt/trustdb.gpg /media/usb_drive/etc/
sudo cp -p /etc/apt/trusted.gpg /media/usb_drive/etc/

```
So you can then just copy the sources files and keys back ;)

(4) What I did for myself is then write a small install script, that will fetch and download and install the software I really want (install.sh):
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
So after I restore my /home folder I just let this run run (sudo sh install.sh) and it will fetch all my "normal" software that I want...

---

### Post by DarinB on 2007-08-24
i reformatted  my external drive to ext3 with gparted.

but it is lost and found and not usable how do i make it usable??

Thanks,
db

---

### Post by ntlam on 2007-08-24
you got troubles now

I once formatted the ext3 and lost everything

---

### Post by DarinB on 2007-08-24
No actually i was reformatting an old hard drive i put in a usb box so i can save my home folder to it.
i just can't seem to get it to not be "lost and found" folder when i tyr to write to it it says not available.

why is that???

---

### Post by hyper_ch on 2007-08-24
do you have it mounted after you reformatted it?

---

### Post by DarinB on 2007-08-24
Sorry if that means just clicking it from my home folder>places i did, that is how the lost and found emblem comes up.

is there another way to mount it???
or is it permissions????
the folder won't delete maybe i can delete via terminal root???

---

### Post by wolfen69 on 2007-08-24
if your imaging program comes with a boot cd, you can back up any drive.(windows,linux) acronis is a good one.

---

