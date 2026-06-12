---
title: "Where to get VLC?"
date: 2005-09-01
forum: Absolute Beginner Talk
---

### Post by _Dan on 2005-09-01
Which repositories? I've been trying to find it for a while as totem and mplayer don't want to play DVDs properly (totem is jerky and i can't get sound on mplayer).

But whether that can be fixed I would like to try VLC anyway.

This is my list at the moment:
> #deb [ftp://mirror.mcs.anl.gov/pub/ubuntu](ftp://mirror.mcs.anl.gov/pub/ubuntu) hoary main restricted universe multiverse
#deb-src [ftp://mirror.mcs.anl.gov/pub/ubuntu](ftp://mirror.mcs.anl.gov/pub/ubuntu) hoary main restricted universe multiverse

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
#deb [ftp://mirror.mcs.anl.gov/pub/ubuntu](ftp://mirror.mcs.anl.gov/pub/ubuntu) hoary-updates main restricted
#deb-src [ftp://mirror.mcs.anl.gov/pub/ubuntu](ftp://mirror.mcs.anl.gov/pub/ubuntu) hoary-updates main restricted

#deb [ftp://mirror.mcs.anl.gov/pub/ubuntu](ftp://mirror.mcs.anl.gov/pub/ubuntu) hoary-security main restricted
#deb-src [ftp://mirror.mcs.anl.gov/pub/ubuntu](ftp://mirror.mcs.anl.gov/pub/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

##archive.ubuntu
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb [http://archive.ubuntu.com/ubuntu/pool](http://archive.ubuntu.com/ubuntu/pool) universe

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

#deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main
#deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
#deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main

#backup Mirror - FAST
deb [ftp://ftp2.caliu.info/backports](ftp://ftp2.caliu.info/backports) hoary-backports main universe multiverse restricted
deb [ftp://ftp2.caliu.info/backports](ftp://ftp2.caliu.info/backports) hoary-extras main universe multiverse restricted 

perhaps it is the [ftp://mirror.mcs.anl.gov/](ftp://mirror.mcs.anl.gov/) ones but they don't seem to be alive  :-|  (so I disabled them)

and the debian-marillat ones gave errors.

Thanks

---

### Post by tealc_sg1 on 2005-09-01
I added the following from "ubuntuguide" to my "sources.list" and have just installed everything related to VLC, it's great , good luck :_)

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

---

### Post by sapo on 2005-09-01
I think that vlc is in universe or multiverse, and you already have those in your list.. just type: 

```
sudo apt-get install vlc
```

I just added those repositories here and used that command and vlc installed

---

### Post by _Dan on 2005-09-01
Thanks but I have just tried that, adding the repositories and replacing them with yours, now it almost works but for this error:
> Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  vlc: Depends: libmodplug0 (>= 1:0.7-1) but it is not installable
E: Broken packages 

It would seem it can't find libmodplug0  :-| whatever that is

EDIT: Seems someone had a similar problem... [http://ubuntuforums.org/showthread.php?t=30676&highlight=libmodplug0](http://ubuntuforums.org/showthread.php?t=30676&highlight=libmodplug0)

---

### Post by _Dan on 2005-09-01
okay... so I found a debian libmodplug0 package here:
[http://packages.debian.org/testing/sound/libmodplug0](http://packages.debian.org/testing/sound/libmodplug0)

install with...
sudo dpkg -i libmodplug0_0.7-4_i386.deb

THEN do...
sudo apt-get install vlc

(then for sound, I copied this from another post...)
apt-get install vlc-plugin-esd
vlc --aout esd

and voila! Now I have working DVD!!! :)

---

### Post by Ceriel Nosforit on 2005-09-12
I'm in deeper poo-poo. 
> vlc:
 Depends: dbus-1 (>=0.23.4) but it is not installable
 Depends: libflac6  but it is not installable
 Depends: libhal0 (>=0.4.0) but it is not installable
 Depends: libmodplug0 (>=1:0.7-1) but it is not installable
 Depends: wxvlc but it is not going to be installed

I'm running Breezy on an amd64 system, and that might have something to do with it. Not that I know. - I'm clueless on what to do about it.  :-(

---

### Post by Ceriel Nosforit on 2005-09-12
```
ceriel@Guerilla1:~$ sudo dpkg -i /home/ceriel/Desktop/debs/dbus-1_0.23.4-6_amd64.deb
Selecting previously deselected package dbus-1.
dpkg: regarding .../debs/dbus-1_0.23.4-6_amd64.deb containing dbus-1:
 dbus conflicts with dbus-1
  dbus-1 (version 0.23.4-6) is to be installed.
dpkg: error processing /home/ceriel/Desktop/debs/dbus-1_0.23.4-6_amd64.deb (--install):
 conflicting packages - not installing dbus-1
Errors were encountered while processing:
 /home/ceriel/Desktop/debs/dbus-1_0.23.4-6_amd64.deb
ceriel@Guerilla1:~$ 
```
How can the package conflict with itself? ='(

---

### Post by servvs on 2005-09-19
[QUOTE=Ceriel Nosforit]I'm in deeper poo-poo. 


I'm running Breezy on an amd64 system, and that might have something to do with it. Not that I know. - I'm clueless on what to do about it.  :-([/QUOTE]
 ya... i got the same problem... this really sux... lol

---

### Post by Ceriel Nosforit on 2005-09-27
Looks like Mplayer will do most of what VLC does. Good enough for me.

---

