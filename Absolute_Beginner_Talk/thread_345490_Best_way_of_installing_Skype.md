---
title: "Best way of installing Skype?"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by willbur on 2007-01-24
Hi everyone

what's the best way of installing Skype on a new edgy installation? So far, I've just used Synaptic to install apps, and it isn't listed there. There are a few conflicting threads on these forums, so I thought I'd ask the question again :wink:

If I perform a manual install, how do I uninstall afterwards?

Many thanks in advance from a complete newbie...

---

### Post by hyper_ch on 2007-01-24
(1) Open Terminal

(2) Nano as sudo the following file /etc/apt/sources.list
```

sudo nano /etc/apt/sources.list

```

(3) At the end of that file add the following:
```

deb http://download.skype.com/linux/repos/debian/ stable non-free

```

(4) Press ctrl-x (for closing the file)

(5) You will then be asked whether to save the changes made --> Press "y"

(6) Then you will be prompted for the file name --> just hit "Enter"

(7) Update your repos
```

sudo apt-get update

```

(8) Install skype
```

sudo apt-get install skype

```

---

### Post by Zzl1xndd on 2007-01-24
I would say [automatix]("http://www.getautomatix.com/wiki/index.php?title=Installation") is probably the quickest way to do it plus its got some other stuff in there that people are often looking for.

---

### Post by AlanRogers on 2007-01-24
[www.getautomatix.com](www.getautomatix.com) - automates installation of Skype, Wine, MS Core Fonts, CD & DVD Codecs and other such useful stuff.
EDIT: Oops, too slow. TweakedEnigma beat me to the very same answer. It must be right though ;)

---

### Post by Canis familiaris on 2007-01-24
Best way to install skype is to first install Automatix and then install skype in its gui
[http://www.getautomatix.com/](http://www.getautomatix.com/)

EDIT: *Tweakedenigma*  and *AlanRogers* both beat me here.

---

### Post by Zzl1xndd on 2007-01-24
w00t 2 people that agree with me :) first time for everything i guess.

---

### Post by willbur on 2007-01-24
Thanks everyone. I've heard that automatix can harm your installation and that it isn't recommended by the Ubuntu staff? Comments, please?

---

### Post by Zzl1xndd on 2007-01-24
> **willbur said:**
> Thanks everyone. I've heard that automatix can harm your installation and that it isn't recommended by the Ubuntu staff? Comments, please?

Can't speak for the staff but its been working really well for me. Although I am more interested in CNR but its not out for any thing but Linspire and Freespire yet. bet I did see somewhere that it is being ported. 

now back to what you asked so far so good for me. the only time i have heard of issues is when upgrading versions of Ubuntu.

---

### Post by hyper_ch on 2007-01-24
The quickest way is not necessarily the best one...

If you use my approach you will also auto-update skype when new releases for linux are available... it won't happen with automatix install...

---

### Post by Zzl1xndd on 2007-01-24
> **sjau said:**
> The quickest way is not necessarily the best one...

If you use my approach you will also auto-update skype when new releases for linux are available... it won't happen with automatix install...

This is also true.

---

### Post by rocknrolf77 on 2007-01-24
Or you could just grab the newest skype at [www.getdeb.net](www.getdeb.net)

---

### Post by willbur on 2007-01-24
Thanks, everyone. Sjau - I've cut and pasted the link you mention

[http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/)

into Firefox and it returns a 'page not found error' and then redirects me to the skype download page. Is this significant, or completely unrelated?

Thanks again...

---

### Post by hyper_ch on 2007-01-24
willbur

you must not use the browser... you must add the "deb ......" line to your sources.list file as I have said in the small "how-to" :)

---

### Post by willbur on 2007-01-24
Thanks, sjau - I just thought I'd check that the link you gave was a good one before I cut and pasted following your instructions. The fact that it gives an error doesn't matter for this install?

---

### Post by hyper_ch on 2007-01-24
No it doesnt :)

---

### Post by willbur on 2007-01-24
OK everyone - thanks for your help (especially sjau!) -  It's all very much appreciated. :D

---

### Post by hyper_ch on 2007-01-24
Once you have succeeded make a reply here :)

---

### Post by willbur on 2007-01-24
OK will do....

---

### Post by willbur on 2007-01-24
OK , all done with 1 question please:

The installation told me that the following packages were installed and are no longer required

libgtk1.2 tcl8.4 libgtk1.2-common imlib-base gdk-imlib11 libungif4g

and tells me to use apt-get autoremove to remove them. Is it OK to do that?

---

### Post by willbur on 2007-01-24
Do I just type in apt-get autoremove, or must I remove each file by name? If this is the case, what is the syntax?

thanks...

---

### Post by hyper_ch on 2007-01-24
just type:
```

sudo apt-get autoremove

```
It's normally save to do that...

---

### Post by willbur on 2007-01-24
Many thanks, once again, sjau - your instrutions were perfect, and now I'm up and running!

I'm certainly not planning on doing so, but how would I remove this newly installed package in the future? :-k

---

### Post by hyper_ch on 2007-01-24
Well, you could remove it by deselecting it from your Add/Remove software program (synaptic or adept) or you could go again to the shell termina:

```

sudo apt-get remove skype

```

However the configuration files will not be deleted that way... you will still ahve them in your /home/user folder :)

P.S.: the shell commands are very powerfull... I have can reinstall my whole computer in about 50min to the current state... I have /home on a seperate partition so all the config files are still there and I have written a little install script which downloads all the programs I "normally" install and use on a regular base :)

---

### Post by willbur on 2007-01-24
Many thanks, once again, sjau. Your help is very much appreciated!

---

### Post by AlanRogers on 2007-01-25
> **sjau said:**
> I have /home on a seperate partition so all the config files are still there and I have written a little install script which downloads all the programs I "normally" install and use on a regular basisCare to share or have this been the subject of a previous thread?

---

### Post by hyper_ch on 2007-01-25
(1) Set a correct sources list

```

# deb cdrom:[Xubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted
# deb cdrom:[Xubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted

deb http://ch.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse
deb-src http://ch.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse

deb http://ch.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse
deb-src http://ch.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse

deb http://ch.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://ch.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu/ edgy-proposed restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ edgy-proposed restricted main multiverse universe


deb  http://mirror.ubuntulinux.nl edgy-seveas all

deb http://archive.canonical.com/ubuntu edgy-commercial main
#deb http://deb.opera.com/opera etch non-free

deb http://download.skype.com/linux/repos/debian/ stable non-free

deb http://archive.canonical.com/ edgy-commercial main

# Beryl
deb http://ubuntu.beryl-project.org/ edgy main

```

Replace "ch.archive.ubuntu.com" with a local mirror :)

(2) Execute the following command to verify Seveas' download repository
```

wget http://mirror.ubuntulinux.nl/1135D466.gpg -O- | sudo apt-key add -

```

(3) Create a install.sh script
```

#!/bin/bash

# Update sources
apt-get update

# Download Skype --> it has problems with the -y option...
apt-get install skype

# Download Java --> User interaction required
apt-get -y install j2re1.4

# --- The downloads below will be auto installed... --- #

#KDE Appz
apt-get -y install konversation konqueror k3b amarok krfb ktorrent kftpgrabber
apt-get -y install kontact kdepim-kio-plugins kgpg

# IMs
apt-get -y install amsn kopete

# IRSSI / OpenSSH
apt-get -y install irssi openssh-server

# GnuMP3d
apt-get -y install gnump3d

# OTR
apt-get -y install python-glade-1.2 python-gtk-1.2

# VmWare Essentials
apt-get -y install linux-headers-`uname -r` build-essential xinetd

# Browsers
apt-get -y install kazehakase mozilla-browser opera flashplugin-nonfree

# Codecs
apt-get -y install libdvdcss2 gstreamer0.10-ffmpeg gstreamer0.10-pitfdll gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui w32codecs mplayer

# Samba
apt-get -y install samba

# Midnight Commander
apt-get -y install mc

# UNRAR
apt-get -y install unrar

# GParted
apt-get -y install gparted

# CheckRootKit
apt-get -y install chkrootkit

# OpenOffice
apt-get -y install openoffice.org

# ImageMagic
apt-get -y install imagemagick

# Numlock & fonts
apt-get -y install numlockx msttcorefonts

# Make Upgrade
apt-get -y upgrade

```
And run it by executing:
```

sudo sh install.sh

```
Skype and Java needs user-interaction... the rest will be auto-downloaded and installed...
I'm using Xfce but I like the KDE appz... so you may want to modify that and add your own favourite packages :)

---

### Post by AlanRogers on 2007-01-25
> **sjau said:**
> [List=1][*] Set a correct sources.list
[*] Verify download repository
[*] Create a install.sh script
[*] Run it[/list]
Skype and Java needs user-interaction... the rest will be auto-downloaded and installed...
so you may want to modify that and add your own favourite packages :)Cool, thanks. Apologies for the brief thread hijack.:oops:

---

### Post by hyper_ch on 2007-01-25
I don't think wollbur does mind :)

Anyway, if you get yourself familiar with apt-get (aptitude) you can very easily re-install your system to the current state if you every decide so :)

Configs are stored in your home folder... and some are stored in /etc (e.g. sources list for apt, config for gnump3d, ....)

---

### Post by willbur on 2007-01-26
Not at all! i'm very happy to learn :D

---

### Post by sparks40 on 2007-01-27
I have read your posts Sjau with great interest. I've performed the installation process as you described.. but Skype will not play back my test message. I am also among the many others who have Skype running under Win XP (dual-booting) with no problem, but find it a pain to have to switch out of Ubuntu just to make or receive a Skype call.

I am using an Asus M2N-MX mb with 1 gig of ram and a AMD processor. My sound card is a SoundBlaster Audigy SE. I have been trying for over a month to get Skype to run under Linux but no luck. I would appreciate any suggestions.

TNX

---

### Post by AlanRogers on 2007-01-27
> **sparks40 said:**
> ... but Skype will not play back my test messageDoes sound work otherwise on your installation? Can you play back an audio CD and hear it fine? Do you use any kind of headset or USB 'phone with Skype? I hesitate to suggest that the problem may not actually be Skype but something it needs to use which isn't configured or installed correctly. Try using that hardware outside of Skype and verify that it works before trouble-shooting Skype any further.

---

### Post by hyper_ch on 2007-01-27
Well, first question of all: does skype run? Can you send and receive messages by skype?

---

### Post by sparks40 on 2007-01-27
TNX Roger and Sjau for your replys. 

1. Yes my sound card is working under Ubuntu for playback.
2. However, I can not hear myself in the mike as I can under Win XP, nor can I successfully use the record sound application.
3. I am using a Plantronics headset which works fine with Skype under XP.
4. I can make outgoing and receive incoming calls under XP but not Ubuntu.
5. I have tried to reconfigure alsamixer several time but it will not allow me to do so.
6. I reinstalled and updated my system this morning, but I still have the same problem.

---

### Post by hyper_ch on 2007-01-27
well, it seems you have rather problems with sound in generell in ubuntu and not just within skype...

---

### Post by sparks40 on 2007-01-27
I think it's in the mixer as I can't change any of the mute selections.I have downloaded the basic instructions for alsamixer but they don't seem to do anything.  Other than that I don't know exactly where to start.

---

### Post by sparks40 on 2007-01-27
The following information may be of some help:

1. My onboard audio (NVidia MCP61 High Definition Audio) is disabled in the BIOS as alsa does not automatically recognize it.
2. I have  a Soundblaster Audigy in the PCI slot which enables me to listen to music and is fully functional under Skype for Win XP.
3. In alsamixer:
________"CAPTUR" appears in red above the "Mic" tab
________The upper left hand corner of the screen indicates Playback and Capture is set to ALL.
4. The Mic. gain is set to appx 80%.

How do these settings compare with yours???

---

