---
title: "Problem with Ubuntu"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by RyviusRan on 2008-03-12
I just recently installed the newest version of ubuntu 7.10

now that everything is installed I am having a problem whenever I want to install programs onto it

i get this error

Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type '“deb' is not known on line 56 in source list /etc/apt/sources.list, E:The list of sources could not be read.'





not sure how I can fix this can anyone offer some advice?

---

### Post by drs305 on 2008-03-12
Please post the results of 
```
cat /etc/apt/sources.list
```

You have a problem on line 56 that is causing the problem. We can fix it once we see what line 56 is.

For a quick fix on your own, if it's only one line that is incorrect, open sources.list in a text editor, place a comment symbol # at the beginning of line 56, and try installing your program again. Of course, the line 56 repository won't be available until it is fixed.
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
sudo gedit /etc/apt/sources.list

```

---

### Post by Rocket2DMn on 2008-03-12
Can you post that file for us?
```
cat /etc/apt/sources.list
```

edit: beaten to it!

---

### Post by RyviusRan on 2008-03-12
this is the whole list just in case....

ryviusran@ryviusran-desktop:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
“deb [http://packages.dfreer.org](http://packages.dfreer.org) feisty main”
“deb [http://packages.dfreer.org](http://packages.dfreer.org) feisty main”
“deb [http://packages.dfreer.org](http://packages.dfreer.org) feisty main”
deb [http://packages.dfreer.org:8080](http://packages.dfreer.org:8080) feisty main
deb [http://packages.dfreer.org:8080](http://packages.dfreer.org:8080) feisty main
deb [http://packages.dfreer.org:8080](http://packages.dfreer.org:8080) feisty main
ryviusran@ryviusran-desktop:~$

---

### Post by Rocket2DMn on 2008-03-12
The problem is with your bottom area, specifically
```
&#8220;deb http://packages.dfreer.org feisty main&#8221;
&#8220;deb http://packages.dfreer.org feisty main&#8221;
&#8220;deb http://packages.dfreer.org feisty main&#8221;
```
All the feisty sources should be commented out (disabled) - not to mention these quotations that shouldn't be there.  The last 6 lines should be:
```
#deb http://packages.dfreer.org feisty main
#deb http://packages.dfreer.org feisty main
#deb http://packages.dfreer.org feisty main
#deb http://packages.dfreer.org:8080 feisty main
#deb http://packages.dfreer.org:8080 feisty main
#deb http://packages.dfreer.org:8080 feisty main
```

Alternatively, if those last 3 line sources support gutsy, you can do as follows.  You only need a source listed once anyway:
```
#deb http://packages.dfreer.org feisty main
deb http://packages.dfreer.org:8080 gutsy main
```

You can edit the file with
```
gksudo gedit /etc/apt/sources.list
```
Save and close, then run
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by RyviusRan on 2008-03-12
thanks for that. now I see that i have 199 updates.......

oh and since I don't want to waste forum space would anyone happen to have a link that tells where to download and install compiz files.

---

### Post by Rocket2DMn on 2008-03-12
Compiz Fusion comes preinstalled on Gutsy, you have to enable it from System->Preferences ->Appearance, Visual Effects tab.

---

### Post by RyviusRan on 2008-03-12
thanks and I was hear on a post and it seems there is a newer version of ubuntu available called hardy or something they didn't specify a link so I was wondering if anyone else had one

---

### Post by Rocket2DMn on 2008-03-12
Hardy Heron is the next release of Ubuntu, version 8.04.  It is still in the alpha 6 stage right now, and is due to be released in April.  Gutsy is still the latest stable release, and you can easily upgrade to Hardy when it comes out in a month.  People using Hardy right now are called "Testing" users since it is not a stable release yet, so you probably want Gutsy.

---

