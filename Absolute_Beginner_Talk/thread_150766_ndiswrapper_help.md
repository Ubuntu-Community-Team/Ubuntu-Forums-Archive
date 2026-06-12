---
title: "ndiswrapper help"
date: 2006-03-26
forum: Absolute Beginner Talk
---

### Post by rhthekida on 2006-03-26
I am trying to install the ndiswrapper-utils or ndisgtk but whenever I try to install either of them in adept, it gives me a BREAK (install). Any help that could be offered would be great, cause I really would like to be able to use my wireless card.

---

### Post by trent dillman on 2006-03-26
Welcome to the forums!

First off, check out [http://ubuntuforums.org/showthread.php?t=25683](http://ubuntuforums.org/showthread.php?t=25683) for a how-to.

---

### Post by rhthekida on 2006-03-26
yea I know all the stuff to deal with installing it, I have been searching around in guides for about a week now, but when I sudo apt-get install ndiswrapper-utils I recieve the following errors

The following packages have unmet dependencies:
   ndiswrapper-utils: Depends: ndiswrapper-modules-1.8 but it is not installable
E: Broken packages

---

### Post by trent dillman on 2006-03-26
Have you enabled multiverse/universe in apt?

---

### Post by rhthekida on 2006-03-26
you know, I'm not even going to pretend to know which that is, so I will go about listingmy repositories here and maybe that can help you help me.

# deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted 

 ## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted 
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted 

 ## Uncomment the following two lines to fetch major bug fix updates produced
 ## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted 
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted 

 ## Uncomment the following two lines to add software from the 'universe'
 ## repository.
 ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
 ## team, and may not be under a free licence. Please satisfy yourself as to
 ## your rights to use the software. Also, please note that software in
 ## universe WILL NOT receive any review or updates from the Ubuntu security
 ## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe 
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe 

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted 
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted 

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe 
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe 

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse 
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse 

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse 

deb [http://ftp.au.debian.org/debian](http://ftp.au.debian.org/debian) unstable main contrib non-free 
deb-src [http://ftp.au.debian.org/debian](http://ftp.au.debian.org/debian) unstable main contrib non-free

---

