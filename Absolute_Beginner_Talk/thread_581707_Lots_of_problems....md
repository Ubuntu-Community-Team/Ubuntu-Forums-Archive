---
title: "Lots of problems..."
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by -Morgoth- on 2007-10-19
I just installed gutsy on my desktop, but there are quite a few problems.
If i open Add/Remove applications, i have to update the applications list and i cant install anything. When i click to install a program, i get an error telling me that the application list is out of date, so it has to be refreshed/updated (again). I do that, but the exact same thing happens again the next time i click on install. Same thing in synaptic package manager.

It wasnt like this when i installed feisty on my laptop a few months ago... anyone knows whats wrong? maybe i have forgotten to do something to make it work?

---

### Post by yabbies on 2007-10-19
sounds like your sources list might be messed up

what's the result of

```
cat /etc/apt/sources.list
```

---

### Post by mlentink on 2007-10-19
Morgoth,

Please go to System>Administration>Software Sources and tell us what repositories are selected.
If you're more familiar with the terminal, do:
```
cat /etc/apt/sources.lst
```
and post the output here

---

### Post by -Morgoth- on 2007-10-19
cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb [http://www.nic.funet.fi/pub/mirrors/archive.ubuntu.com/](http://www.nic.funet.fi/pub/mirrors/archive.ubuntu.com/) gutsy multiverse restricted universe main
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse



Edit: Now i get :
cat /etc/apt/sources.lst
cat: /etc/apt/sources.lst: No such file or directory

---

### Post by mlentink on 2007-10-19
I'd comment out the relevant lines and try again
```
sudo gedit /etc/apt/sources.lst
```

---

### Post by yabbies on 2007-10-19
replace everything with this sources list:



deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the ‘backports’
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical’s
## ‘commercial’ repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.

## ‘commercial’ repository in Gutsy is not working yet
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy commercial
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy commercial

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

##################################################
##################################################
##ffmpeg of ubuntu is slower then molasses in January on the arctics
##Alternative resource for Multimedia support like ffmpeg
#is meant for Debian But works fine on my Gutsy Gibbon
##use at your own risk
##See: [http://debian.video.free.fr/index.html](http://debian.video.free.fr/index.html)
##get the apt GPG key from here : [http://debian.video.free.fr/faq.html](http://debian.video.free.fr/faq.html)
deb [ftp://ftp.uni-kl.de/debian-multimedia/](ftp://ftp.uni-kl.de/debian-multimedia/) stable main
##############################################
##############################################

---

### Post by mlentink on 2007-10-19
Sorry...
didn catch your edit that time. Could you try the last command? The gedit one?

---

### Post by mlentink on 2007-10-19
> **yabbies said:**
> replace everything with this sources list:

Off topic: Yabbies, why are you using the dutch mirror when you're in Missouri?

---

### Post by corney91 on 2007-10-19
> **mlentink said:**
> I'd comment out the relevant lines and try again
```
sudo gedit /etc/apt/sources.lst
```

```
**gk**sudo gedit /etc/apt/sources.lst
```;)
[http://psychocats.net/ubuntu/graphicalsudo]("http://psychocats.net/ubuntu/graphicalsudo")

---

### Post by mlentink on 2007-10-19
Dude, have it your way.....

But:

> Why is it an issue?
Well, to be perfectly honest, most of the time it isn't. For a lot of applications, you can run them the improper way--using sudo for graphical applications and see no adverse side effects.

That's what the man said...

---

### Post by yabbies on 2007-10-19
ha I didn't even see that
I'm currently on windows work computer
and got the sources.list off Tuxicity's website.

[http://tuxicity.wordpress.com/sourceslist-for-gutsy-gibbon/]("http://tuxicity.wordpress.com/sourceslist-for-gutsy-gibbon/")

---

### Post by -Morgoth- on 2007-10-19
Thanks, seems to be working with that sources list

---

### Post by bapoumba on 2007-10-19
I'd personally remove the debian-multimedia repo.

---

### Post by corney91 on 2007-10-19
> **mlentink said:**
> Dude, have it your way.....

But:



That's what the man said...

Sorry - just in a picky mood today:p

---

