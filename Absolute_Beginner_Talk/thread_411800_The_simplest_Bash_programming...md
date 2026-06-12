---
title: "The simplest Bash programming.."
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by Visti on 2007-04-17
Hi, I was going to write a shell scripts to optimize my install time (installing a bunch of apps by exectuting the scripts) when I install a clean system, but how would I go about achieving this? I surfed around a bit and read some bash scripting pages, but it seems what I'm looking for is Ubuntu/Debian specific or..?

For example: Step one of the script is to get a few desired apps, let's say ScummVM and Gnomebaker, just for kicks. These are in the repositories, so something like:
```

#! /bin/bash
echo Installing ScummVM!
sudo aptitude install scummvm
echo Done!
&

```

..would do it, right? But what when I have to agree to install the app by typing 'Yes'? Hwo do I automate that? And also is there some way to turn off the echo for a while in bash to do some tasks with text scrolling all madly about? Anyway, these were the simple things I was wondering about. It must be possible, Envy seems to do basically the same thing.. Or am I wrong here?

---

### Post by hyper_ch on 2007-04-17
Well, I use this:

```

#!/bin/bash

aptitude update
aptitude -y upgrade

# Skype
aptitude -y install skype

# Java
aptitude -y install sun-java6-jre sun-java5-jre

#KDE Appz
aptitude -y install kopete konversation konqueror k3b amarok krfb ktorrent
aptitude -y install kftpgrabber kate kontact kdepim-kio-plugins kgpg
aptitude -y install akregator gdb


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

# various
aptitude -y install whois phpmyadmin mysql-server mysql-client libmysqlclient15-dev

```

Instead of aptitude you can use apt-get (depends on whether you want to have recommended packages also installed).

I split it up into groups but you can issue this with one big command. Furhter I put java and skype on top because they need user input...

The  -y  switch makes that you aren't asked whether you want to install that piece of software...

And I run it then by

```

sudo install.sh

```

What is lacking so far is adding extra repos to the /etc/sources.list and importing the keys for those repos... so far I do this manually but I will enhance my little script later on.

---

### Post by braddcadd on 2007-04-17
here is the link that got me started bash scripting, [http://www.linuxcommand.org/wss0010.php](http://www.linuxcommand.org/wss0010.php)

Good luck!

---

### Post by Terl on 2007-04-17
> **braddcadd said:**
> here is the link that got me started bash scripting, [http://www.linuxcommand.org/wss0010.php](http://www.linuxcommand.org/wss0010.php)

Good luck!

That is a very nice link!  Thanks for posting it.

---

### Post by ThrobbingBrain66 on 2007-04-17
I asked the same thing here a while back. Here is the thread, I think it'll help:

[http://ubuntuforums.org/showthread.php?t=290764](http://ubuntuforums.org/showthread.php?t=290764)

---

### Post by rich.bradshaw on 2007-04-17
remember to type

chmod +x NAMEOFSCRIPT

that way it is executable.

to run type

./NAMEOFSCRIPT

---

### Post by Limitlesschannels on 2007-04-18
yeah, listen to rich.bradshaw, I was amazed at how long it took me to figure out why basic script execution wasn't working, heheheh

---

### Post by hyper_ch on 2007-04-18
it needn't to be executable if you do "sh script.sh" (I think)

---

