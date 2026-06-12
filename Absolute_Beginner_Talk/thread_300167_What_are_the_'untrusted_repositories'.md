---
title: "What are the 'untrusted repositories'?"
date: 2006-11-15
forum: Absolute Beginner Talk
---

### Post by Biggus on 2006-11-15
Hi there.

I don't want to appear any thicker than usual, but a few chaps are having a chinwag over in another thread, with regards to something called the 'untrusted repositories'.

[http://www.ubuntuforums.org/showthread.php?t=297814]("http://www.ubuntuforums.org/showthread.php?t=297814")

Normally, I would have just asked in that thread, but it's all becoming a bit too high-fulootin' (technically speaking) for me to interject with my noobish questions.

Basically, I've been installing a lot of stuff from a few different places.

1) Applications->System Tools->Adept Manager
2) Applications->Add/Remove
3) System->Administration->Synaptic Package Manager

And I might not have properly kept track of it all, so what I would like to know is, are these three 'repositories' (sorry if that's the incorrect terminology, it's only my third day of Ubuntu, and I have had my brain numbed through years of using M$ products) I have listed above 'trusted'? Is there any possibility I might have installed something I shouldn't have?

---

### Post by earobinson on 2006-11-15
untrusted repositories would really be anything thats not shipped by the main dev team eg backports and such.

doing a search for sources.list on the forms should find you a bunch of them.

and just for convenience here is my /etc/apt/sources.list> # Ubuntu supported packages (GPG key: 437D05B5)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-proposed main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-proposed main restricted

# Ubuntu community supported packages (GPG key: 437D05B5)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-proposed universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-proposed universe multiverse

# Ubuntu backports project (GPG key: 437D05B5)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

# CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu servers.
# RealPlayer10, Opera and more to come.)
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

# Seveas&#8217; packages (GPG key: 1135D466)
deb [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) edgy-seveas all
deb-src [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) edgy-seveas all

#######################
##### UNSUPPORTED #####
#######################

##### AUTOMATIX 2
# Use the following commands to make it work
# gpg --keyserver hkp://wwwkeys.eu.pgp.net --recv-keys 18B52FE3521A9C7C
# gpg --armor --export 521A9C7C > keyName.gpg
# sudo apt-key add keyName.gpg
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

#AUTOMATIX REPOS START

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) dapper main

deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
#AUTOMATIX REPOS END


#######################
##### UNSUPPORTED #####
#######################

##### AUTOMATIX 2
# Use the following commands to make it work
# gpg --keyserver hkp://wwwkeys.eu.pgp.net --recv-keys 18B52FE3521A9C7C
# gpg --armor --export 521A9C7C > keyName.gpg
# sudo apt-key add keyName.gpg
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main
Note: unsupported = untrusted

---

### Post by GStubbs43 on 2006-11-15
Repositories, or repos, are in your /etc/apt/sources.list, such as earobinson posted, if you haven't changed that, you probably have all trusted repos.

> **Biggus said:**
> 
1) Applications->System Tools->Adept Manager
2) Applications->Add/Remove
3) System->Administration->Synaptic Package Manager

Those are ways of installing, not repositories. Other ways are by going into the terminal, or konsole for kubuntu, and using aptitude (or apt-get.)

---

### Post by Biggus on 2006-11-15
Ahhhh.

> deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse

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

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

#AUTOMATIX REPOS START
deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) dapper main
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse
#AUTOMATIX REPOS END


My own sources.list appears to only have 'Automatrix' installed as an unsupported item, everything else appears (to me at least) to be very much 'trusted'.

Many thanks for your help chaps.

---

