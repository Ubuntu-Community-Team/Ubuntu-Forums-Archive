---
title: "Installed and online- which updates/upgrades should I use"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by phatdad on 2007-09-20
Hoping someone can advise me. I tried Ubuntu a while ago, but had to give up when upgrading caused problems. I ended up with a broken X server (I think), that i couldn't sort out. I gave up for a while but now I'm back on Ubuntu. It's 6.10 Edgy. I've got it installed, and loaded up my Sagem USB modem via the eagle atm route.

I have installed Firestarter via Synaptic, and opened all the available repositories via the tick box method in Synaptic. Now the update manager is saying there are 181 updates, and a new distribution 7.04 available. 

Last time I just upgraded as I was prompted led to the X server blue screen. I want to try and keep things going this time. I spent sometime getting Ubuntu running for my set up (eg Nvidea drivers etc). I want to hold on with the extras this time, till I'm up to date and running with a stable OS.

So my question is, what repositories should I have open, should I install all the updates or upgrade, and what sort of download sizes are involved in all this?

Actually, that's a few questions. Hope someone can help

Here's output from gksudo gedit /etc/apt/sources.list

deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/ edgy main restricted
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy main restricted multiverse universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy main restricted multiverse universe

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-updates main restricted multiverse universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-updates main restricted multiverse universe

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted multiverse universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted multiverse universe
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

Thanks in advance
pd

---

### Post by maryjanua on 2007-09-20
i installed feisty 7.04 for the 1st time last friday and there was 180mb of updates if thats any help:)

---

### Post by phatdad on 2007-09-20
Thanks. That would take me a while to download. Are you, by any chance,  using a similar set up (ie Sagem USB modem, NVidea etc) and where there any problems?

---

### Post by maryjanua on 2007-09-20
sorry man im using an ati card with a celeron d 3.2 and a bt homehub on dsl i got it at about 700kb/s so it didnt take very long. iv had a few problems with sound but they got fixed by folk helping me in here and my video card is  not giving me the full experience but ati cards seem to be an ongoing problem theres plenty of guides for installing nvidia stuff
regards mj :)

---

