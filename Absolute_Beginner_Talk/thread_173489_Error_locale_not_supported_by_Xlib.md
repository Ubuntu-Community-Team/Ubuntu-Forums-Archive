---
title: "Error locale not supported by Xlib"
date: 2006-05-10
forum: Absolute Beginner Talk
---

### Post by Isoss on 2006-05-10
Weird error given by terminal every time trying to install or open anything:
for example: I am trying to open bluefish:
```

(bluefish:17165): Gdk-WARNING **: locale not supported by Xlib

(bluefish:17165): Gdk-WARNING **: cannot set locale modifiers

```

Openeing source.list with gedit:
```
(gedit:17191): Gdk-WARNING **: locale not supported by Xlib

(gedit:17191): Gdk-WARNING **: cannot set locale modifiers

```
Or trying to open Automatic:
```
(zenity:17121): Gdk-WARNING **: locale not supported by Xlib

(zenity:17121): Gdk-WARNING **: cannot set locale modifiers

```
.......

WHAT THE HELL!!! 

These are my repositories:
```
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src http://archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
## deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu/ breezy universe main restricted multiverse

deb http://wine.lowvoice.nl/apt breezy main
deb-src http://wine.lowvoice.nl/apt breezy main

deb http://deb.opera.com/opera/ etch non-free

deb http://kubuntu.org/packages/kde351 breezy main

deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://koti.mbnet.fi/~ots/ubuntu/ breezy/
deb-src http://koti.mbnet.fi/~ots/ubuntu/ breezy/

deb http://theli.free.fr/packages/breezy/ ./
## created by arniewinechanged

```

PLEASE HELP ME!

---

### Post by Isoss on 2006-05-10
Synaptic is giving me this:

The following problems were found on your system:
W: Couldn't stat source package list [http://theli.free.fr](http://theli.free.fr) ./ Packages (/var/lib/apt/lists/theli.free.fr_packages_breezy_._Packages) - stat (2 No such file or directory)

---

### Post by Ptero-4 on 2006-05-10
Your locale problems are b/c you don't seems to have the locale packages installed correctly. And the synaptic one is b/c the last repo in your sources.list is unavailable (probably the server is down).

---

### Post by Isoss on 2006-05-10
Ok... What can I do then?

---

### Post by Isoss on 2006-05-10
OK, I searched for my problem and found these:
[http://ubuntuforums.org/showthread.php?t=50040&highlight=locale+Xlib](http://ubuntuforums.org/showthread.php?t=50040&highlight=locale+Xlib)
[http://ubuntuforums.org/showthread.php?t=43467&highlight=locale+Xlib](http://ubuntuforums.org/showthread.php?t=43467&highlight=locale+Xlib)

in both, humina said:
```
This tells you that your locale is not set to en_US or en_GB or whatever. It is actually set to some language called C. You can see this by typing locale -a. The output shows your first locale is C. I don't know how to fix this, but this is where the problem lies.
```

he's right ... this is how it looks when I type locale -a:
```
C
en_AU.utf8
en_BW.utf8
en_CA.utf8
en_DK.utf8
en_GB.utf8
en_HK.utf8
en_IE.utf8
en_IN
en_IN.utf8
en_NZ.utf8
en_PH.utf8
en_SG.utf8
en_US.utf8
en_ZA.utf8
en_ZW.utf8
POSIX

```

Does any body know how to fix this?

---

### Post by Isoss on 2006-05-10
Hello ... somebody help!

---

