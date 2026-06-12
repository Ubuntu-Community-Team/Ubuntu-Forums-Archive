---
title: "A few simple questions"
date: 2006-07-27
forum: Absolute Beginner Talk
---

### Post by GuitarHero on 2006-07-27
First of all I'd like to fix this:
> W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages)

I get a ton of those errors every time I do sudo apt-get update.  I think I messed something(or a bunch of things up) when enabling extra repositories.  I kinda just winged it, I did it once a while ago and thought I knew how to do it.

Also I think this problem is related.  Im not seeing some programs I should be seeing in the package manager.  I've heard Rosegarden(an old version) is in the repos but its not anywhere to be found in mine.  Also the limewire alternative(frostwire or something)?  I'm guessing I didnt actually enable anything.

Also how do I know the name of the program as far as the command line goes.  I installed Limwire with alien but now I cant seem to uninstall it, and it wont run.

Thanks in advance.

---

### Post by ovimunt on 2006-07-27
Ok, try replacing the whole sources.list file with the default one.

Do this:

> 
sudo gedit /etc/apt/sources.list


Now delete EVERYTHING in there and replace it with:

```

## Major bug fix updates produced after the final release of the 
## distribution. 
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted 
 
## Uncomment the following two lines to add software from the 'universe' 
## repository. 
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## universe WILL NOT receive any review or updates from the Ubuntu security 
## team. 
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe 
 
## Uncomment the following two lines to add software from the 'backports' 
## repository. 
## N.B. software from this repository may not have been tested as 
## extensively as that contained in the main release, although it includes 
## newer versions of some applications which may provide useful features. 
## Also, please note that software in backports WILL NOT receive any review 
# or updates from the Ubuntu security team. 
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse 
 
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted 
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted 
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe 
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
```

Now save the file and do:

> 
sudo aptitude update

That should be it.

---

### Post by ovimunt on 2006-07-27
Or instead, if you'd like some nice additional repositories, you can replace the content of the sources.list with this:

```

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse




## dapper-commercial by canonical
## currently has realplay (realplayer 10) and opera (opera 9)
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

## Cipherfunk multimedia packages (GPG key: 33BAC1B3)
deb [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) dapper main
deb-src [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) dapper main

## Dapper PLF
## only uncomment it if you need it
## deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free
## deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free

## Bleeding edge (official) wine repository for Dapper
## only uncomment it if you need it
# deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
# deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

## skype (official)
## only uncomment it if you need it
## deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

deb [http://mirrors.ecology.uni-kiel.de/debian/debian-multimedia](http://mirrors.ecology.uni-kiel.de/debian/debian-multimedia) stable main
deb-src [http://mirrors.ecology.uni-kiel.de/debian/debian-multimedia](http://mirrors.ecology.uni-kiel.de/debian/debian-multimedia) sid main

deb [http://theli.free.fr/packages/](http://theli.free.fr/packages/) dapper listen

```

This is my sources.list file. Yet, be careful! Some of these repositories need authentification and at the moment I can't find the file where I saved the list for later refference. :D

---

### Post by GuitarHero on 2006-07-27
Thanks man, and is that with or without extra repo's enabled?, ah you got to it before i asked, thanks.

---

### Post by ovimunt on 2006-07-27
That's everything enabled. 

By the way, I need to edit my previous two posts, check the changes!

---

