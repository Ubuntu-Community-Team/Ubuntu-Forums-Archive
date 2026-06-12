---
title: "[SOLVED] installing firefox, linux is hard :("
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by vertozia on 2008-03-23
well its my 2nd day of linux, im loving it, but why did installation have to be so hard,,,

can someone tell me what to do step by step, when i tried ./configure on the firefox extracted tarball it told me no such command, 

then when i tried:

```
loris@loris-desktop:~$ **sudo apt-get install mozilla-firefox**
```

i got:

```
Reading package lists... Done
Building dependency tree... Done
Package mozilla-firefox is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mozilla-firefox has no installation candidate
```


please help

ps: im also having issues with my sources file... here it is


```
# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ dapper main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

# Uncomment the following two lines to add software from the 'universe'
# repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://us.archive.ubuntu.com/ubuntu/ dapper universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu dapper-security main
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu dapper-security main
# deb http://security.ubuntu.com/ubuntu dapper-security universe
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe

 deb http://in.archive.ubuntu.com/ubuntu breezy main restricted
 deb http://in.archive.ubuntu.com/ubuntu breezy-updates main restricted
 deb http://in.archive.ubuntu.com/ubuntu hoary universe

deb cdrom:[Kubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted
```

---

### Post by ghost_ryder35 on 2008-03-23
1. Download [http://download.mozilla.org/?product=firefox-2.0.0.12&os=linux&lang=en-US](http://download.mozilla.org/?product=firefox-2.0.0.12&os=linux&lang=en-US)

2. Then follow this guide, [http://www.ubuntugeek.com/howto-install-firefox-3-beta-2-in-ubuntu-710-gutsy-gibbon.html](http://www.ubuntugeek.com/howto-install-firefox-3-beta-2-in-ubuntu-710-gutsy-gibbon.html) , and just change the filenames he refers to, to your file names eg. firefox-2.0.0.12

---

### Post by ugm6hr on 2008-03-23
Which version of Linux / Ubuntu have you installed?

What hardware do you have?

Firefox has been default installed in Ubuntu for as long as I recall.

You seem to have a bizarre combination of sources, with breezy and hoary.  The CD seems to link to Kubuntu 6.06 (does Kubuntu not have Firefox?)

How did you install Linux?

Honestly, if you are unsure, I would suggest trying the latest regular Ubuntu (Ubuntu Gutsy).  It will probably be a lot easier.

---

### Post by vertozia on 2008-03-23
Error 404 - Not Found


the links arent complete, the ... breaks them


and i run kubuntu 6.06 LTS, i have a ghetto 700mgz pc, 15gb fireball HD


edit: i dont know what the problem is tho, i went to add remove and my firefox is greyed out, so i think it is restricted, i edited my sources file and it started crashing (the add remove) so then i just changed it back to normal

---

### Post by ghost_ryder35 on 2008-03-23
[http://download.mozilla.org/?product=firefox-2.0.0.12&os=linux&lang=en-US](http://download.mozilla.org/?product=firefox-2.0.0.12&os=linux&lang=en-US)

[http://www.ubuntugeek.com/howto-install-firefox-3-beta-2-in-ubuntu-710-gutsy-gibbon.html](http://www.ubuntugeek.com/howto-install-firefox-3-beta-2-in-ubuntu-710-gutsy-gibbon.html)

---

### Post by Darganot on 2008-03-23
You need to fix your sources.list BADLY... if you want one of us to do it, we can, but we need to know A LOT of info about the type of ubuntu you're running, your hardware, and the kinds of programs you use regularly (e.g. codecs, wine, etc.).

Firefox should be installed by default, if not some other minimal browser.

---

### Post by Jimmyfj on 2008-03-23
Instead of getting a headage on a firefox install, which you just need to fire up Synaptic to install you could try the much faster swiftfox:

[http://getswiftfox.com/deb.htm](http://getswiftfox.com/deb.htm)

Just download the version specific to your CPU and dbl-click on the .deb file - Ubuntu will do the rest for you.

---

### Post by wolfen69 on 2008-03-23
you may want to replace your repos with these:
```
## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://packages.medibuntu.org/ dapper free non-free

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.) 
deb http://archive.canonical.com/ubuntu dapper-commercial main
```
save file.

then:
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -
sudo apt-get update
```

---

### Post by steveneddy on 2008-03-23
> **vertozia said:**
> 


the links arent complete, the ... breaks them




Just click the links, don't copy them.

Clickable links, the [COLOR="DarkOrange"]different colored words[/COLOR] mean that it is probably a link that you can click and it will take you to another web page.

---

### Post by TheWizzard on 2008-03-23
> **ghost_ryder35 said:**
> 1. Download [http://download.mozilla.org/?product=firefox-2.0.0.12&os=linux&lang=en-US](http://download.mozilla.org/?product=firefox-2.0.0.12&os=linux&lang=en-US)


please teach people to use the repo's

---

### Post by TheWizzard on 2008-03-23
> **vertozia said:**
> 
ps: im also having issues with my sources file... here it is


this happen when your computer is not wired to the internet when you install. 

judt fix your sources and apt-get works!

---

### Post by steveneddy on 2008-03-23
Dude, firefox is in the repos.

Go to Synapric Package Manager and search for firefox.

Click install then apply.

Easy.

---

### Post by TheWizzard on 2008-03-23
> **steveneddy said:**
> Dude, firefox is in the repos.

Go to Synapric Package Manager and search for firefox.

Click install then apply.

Easy.

please read the initial post. his sources list is all commented out.

---

### Post by aysiu on 2008-03-23
> **TheWizzard said:**
> please read the initial post. his sources list is all commented out.
And possibly for older, unsupported versions of Kubuntu (5.04 and 5.10).

---

### Post by TheWizzard on 2008-03-24
> **aysiu said:**
> And possibly for older, unsupported versions of Kubuntu (5.04 and 5.10).

he's using dapper

---

### Post by vertozia on 2008-03-24
hey there, sorry for not replying my isp screwed me over and i had no internet, anyways, i dont have synaptic, i'm really new to linux so i barely know anything so far, my pc WAS connected while installing ubuntu.

so is it safe to use the source file list i was given?

thanks in advance

---

### Post by aysiu on 2008-03-24
Copy and paste these commands into [the terminal](http://www.psychocats.net/ubuntu/terminal) one line at a time (so copy, paste, hit *Enter*; repeat). If you get an error message, copy and paste the error message back here: ```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.old
sudo nano /etc/apt/sources.list
``` This last command will open a new (empty) sources.list file in a text editor called Nano (I would use a graphical text editor, but I have no idea if you're using Kubuntu, Xubuntu, or Ubuntu--Nano is universal and will work for all three). In the text editor, paste this chunk of code: ```
## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu dapper universe
deb-src http://archive.ubuntu.com/ubuntu dapper universe

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

deb http://archive.ubuntu.com/ubuntu dapper multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper multiverse

deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse 
``` Then save the file by pressing Control-X, Y, Enter.

TheWizzard seems convinced that you have Dapper installed, but I saw sources in your original list for Breezy and Hoary, so just to be safe, paste in these commands: ```
sudo apt-get update
sudo apt-get dist-upgrade
``` If you truly had Dapper (or Ubuntu 6.06) already installed, pretty much nothing should happen with that second command. If you had Breezy (5.10) or Hoary (5.04) installed, the second command should upgrade you to Dapper (6.06).

Lastly, to install Firefox, paste in ```
sudo apt-get install firefox
```

---

### Post by vertozia on 2008-03-24
whoa that was a speedy reply! thanks

well i got to this step and i'm getting this, should i continue, as far as i know it says Kubuntu 6.06 LTS for your PC on my disc...anyways


```

loris@loris-desktop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  libatk1.0-0 libgpod0 libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libifp4
  libjasper-runtime libpango1.0-0 libpango1.0-common libsdl1.2debian
  libsdl1.2debian-alsa libtunepimp3 libvisual-0.4-0 linux-image-2.6.15-51-386
  linux-restricted-modules-2.6.15-51-386 python-qt3 ruby ruby1.8
The following packages will be upgraded:
  acpi-support adept amarok amarok-xine app-install-data apt apt-utils
  base-files bind9-host binutils binutils-static bsdutils cpio cupsys
  cupsys-bsd cupsys-client dbus debconf debconf-i18n dnsutils dpkg dpkg-dev
  dselect dvd+rw-tools e2fslibs e2fsprogs file gnupg gtk2-engines-gtk-qt gzip
  hal imagemagick info initramfs-tools iptables k3b kate kcontrol kde-guidance
  kdebase-bin kdebase-data kdebase-kio-plugins kdelibs-bin kdelibs-data
  kdelibs4c2a kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd
  kdeprint kdesktop kdm kdnssd kfind khelpcenter kicker klipper klogd
  kmenuedit koffice-data koffice-libs konqueror konqueror-nsplugins konsole
  konversation kopete kpf kppp krdc krfb krita krita-data ksmserver ksplash
  ksysguard ksysguardd ktorrent kubuntu-artwork-usplash
  kubuntu-default-settings kubuntu-desktop kubuntu-docs kwin language-pack-en
  language-pack-en-base language-pack-kde-en language-pack-kde-en-base
  language-selector-common language-selector-qt libaudio2 libavahi-client3
  libavahi-common-data libavahi-common3 libavahi-qt3-1 libbind9-0 libblkid1
  libc6 libc6-dev libc6-i686 libcairo2 libcomerr2 libcupsimage2 libcupsys2
  libcurl3 libcurl3-gnutls libdbus-1-2 libdbus-glib-1-2 libdbus-qt-1-1c2
  libdns21 libexif12 libflac++5c2 libflac7 libfreetype6 libgd2-noxpm libgeoip1
  libglib2.0-0 libgnutls12 libgpgme11 libgstreamer-plugins-base0.10-0
  libhal-storage1 libhal1 libisc11 libisccc0 libisccfg1 libjasper-1.701-1
  libk3b2 libkonq4 libkrb53 liblwres9 libmagic1 libmagick9 libmodplug0c2
  libmusicbrainz4c2a libmysqlclient15off libnspr4 libnss3 liboggflac3 libpcre3
  libperl5.8 libpng12-0 libpoppler1 libpoppler1-qt libpq4 libqt3-mt libruby1.8
  libsmbclient libsndfile1 libsnmp-base libsnmp9 libspeex1 libss2 libssl0.9.8
  libtag1c2a libtheora0 libtiff4 libtunepimp2c2a libuuid1 libvorbis0a
  libvorbisenc2 libvorbisfile3 libwpd8c2a libx11-6 libxfont1 libxml2 linux-386
  linux-image-386 linux-restricted-modules-386 linux-restricted-modules-common
  locales login lvm2 mount mysql-common openoffice.org openoffice.org-base
  openoffice.org-calc openoffice.org-common openoffice.org-core
  openoffice.org-draw openoffice.org-impress openoffice.org-java-common
  openoffice.org-kde openoffice.org-l10n-en-us openoffice.org-math
  openoffice.org-writer openssh-client openssl passwd pcmcia-cs perl perl-base
  perl-modules perl-suid pmount poppler-utils popularity-contest ppp
  python-apt python-pyorbit python-uno python2.4 python2.4-apt python2.4-dbus
  python2.4-dev python2.4-examples python2.4-gdbm python2.4-libxml2
  python2.4-minimal python2.4-pyorbit python2.4-tk readahead rsync
  samba-common screen slocate smbclient sysklogd tar tcpdump tk8.4
  ttf-opensymbol ubuntu-base ubuntu-minimal ubuntu-standard udev unzip
  util-linux vim vim-common vim-runtime w3m wpasupplicant xinit
  xserver-xorg-core xserver-xorg-input-mouse
233 upgraded, 18 newly installed, 0 to remove and 0 not upgraded.
Need to get 323MB of archives.
After unpacking 162MB of additional disk space will be used.
Do you want to continue [Y/n]?       
```

should i continue?

---

### Post by aysiu on 2008-03-24
If you have a high-speed connection and don't mind downloading 323 MB, then, yes, you should continue. If not, just skip that and do ```
sudo apt-get install firefox
```

---

### Post by Darganot on 2008-03-24
yes

It's not as dramatic as it seems  :)

---

### Post by forrestcupp on 2008-03-24
Also, for future reference, the reason you don't have Synaptic is that you are using Kubuntu.  In Kubuntu, they include Adept, which is another GUI frontend for installing programs.

---

### Post by vertozia on 2008-03-24
i thank you all for your quick help and support!

---

### Post by vertozia on 2008-03-24
yeah, but half the things in adept were greyed out, ill wait for my updates to complete. is there a way to install rpm's through adept?

---

### Post by aysiu on 2008-03-24
> **vertozia said:**
> yeah, but half the things in adept were greyed out, ill wait for my updates to complete. is there a way to install rpm's through adept?
What things in Adept are greyed out? Can you give an example of a package name?

And, yes, there are ways to install RPMs (not through Adept), but you usually don't need to. What software do you think you need RPMs for?

---

### Post by vertozia on 2008-03-24
well my update is not done so i cant really open adept, but for example firefox was grayed out, the mp3 plugins (xine) etc. i got my plugins going but not the firefox, so i'm eager for this update to finish. But i believe the only reason they were grayed out was because my sources file was messed and those lines were commented, (the ones for the restricted applications)

---

### Post by vertozia on 2008-03-24
thanks all works fine now!:popcorn:

---

### Post by stchman on 2008-03-24
> **ugm6hr said:**
> Which version of Linux / Ubuntu have you installed?

What hardware do you have?

Firefox has been default installed in Ubuntu for as long as I recall.

You seem to have a bizarre combination of sources, with breezy and hoary.  The CD seems to link to Kubuntu 6.06 (does Kubuntu not have Firefox?)

How did you install Linux?

Honestly, if you are unsure, I would suggest trying the latest regular Ubuntu (Ubuntu Gutsy).  It will probably be a lot easier.

Kubuntu does not have Firefox installed by default.  Kubuntu uses Konquerer instead.

---

