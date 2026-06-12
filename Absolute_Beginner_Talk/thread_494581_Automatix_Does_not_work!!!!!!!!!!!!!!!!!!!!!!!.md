---
title: "Automatix Does not work!!!!!!!!!!!!!!!!!!!!!!!"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by swoll1980 on 2007-07-07
You may have seen me post commits about automatix recently warning people not to use it. I got    
a lot of negative responses from some loyal automatix fans claiming the product was not damaging to the Ubuntu OS. I thought maybe it was a coincidence, maybe I was being to hard on them.  Just to prove to my self that it was automatix and not a "newbie mistake" I tried installing some stuff on a fresh ubi install with Automatix and sure enough it's 3 for 3 when it comes to hosing my package install. Way to go Automatix you've done it again. This is a new one for me this time anyone know how to fix this one,( I attached picture of error message) by any chance? Some help would be appreciated. I know with out a doubt now that it is in deed Automatix that is doing it. It's not a coincidence that all three times I've used it my installer broke.

---

### Post by swoll1980 on 2007-07-07
oops forgot the picture

---

### Post by misfitpierce on 2007-07-07
Well it did not mess up ubuntu on my laptop. In fact its a great tool thats useful to beginners as well as lazy people looking for a lot of pre-compiled packages to just install. I recommend it and have not had 1 prob for months from automatix.

---

### Post by orb9220 on 2007-07-07
What you need to do is open your /etc/apt/sources.lst and find the line with E:Type 'O;;deb in it and post it here or your complete sources.lst

---

### Post by swoll1980 on 2007-07-07
Do you know how to fix this, It doesn't matter if it did not do this to yours it did do it to mine so apperently it does break installers. Some people get killed in car accidents, so because I didn't that means what? That it doesn't happen?

---

### Post by swoll1980 on 2007-07-07
> **orb9220 said:**
> What you need to do is open your /etc/apt/sources.lst and find the line with E:Type 'O;;deb in it and post it here or your complete sources.lst

ok I'll do that

---

### Post by swoll1980 on 2007-07-07
> **orb9220 said:**
> What you need to do is open your /etc/apt/sources.lst and find the line with E:Type 'O;;deb in it and post it here or your complete sources.lst

here it is

---

### Post by swoll1980 on 2007-07-07
I uploaded it but it did not show up I'll try again

---

### Post by swoll1980 on 2007-07-07
Ill do it this way

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

#AUTOMATIX REPOS START

O::deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) feisty main

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
#AUTOMATIX REPOS END

---

### Post by angkor on 2007-07-07
> **swoll1980 said:**
> http://wine.lowvoice.nl/apt[/url] feisty main



Just delete the O:: in front of this line, save you sources.list and do a sudo apt-get update. You'll be able to use the package manager again.

---

### Post by swoll1980 on 2007-07-07
every thing working great thanks

---

### Post by macogw on 2007-07-07
We don't recommend Automatix here or on #ubuntu on IRC because it's known to be a source of issues.  Try going on #ubuntuforums or #ubuntu and typing (all by itself) !automatix and read what ubotu says.

---

