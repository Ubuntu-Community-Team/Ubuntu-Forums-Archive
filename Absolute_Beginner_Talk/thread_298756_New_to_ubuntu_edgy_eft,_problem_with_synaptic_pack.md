---
title: "New to ubuntu edgy eft, problem with synaptic package manage, any ideas?"
date: 2006-11-13
forum: Absolute Beginner Talk
---

### Post by matt_tee on 2006-11-13
[B]Hi, an old xp user, finally jumped ship. What a breath of fresh air! why didn't I do it sooner!:confused: 

Anyway, the problem is with the synaptic package manager.

I tried to add in some new reositories, and i now get this error message when reloading :

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://archive.ubuntu.com/ubuntu/dists/edgy-updates/Release:](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/Release:) Unable to find expected entry  deb-src/binary-i386/Packages in Meta-index file (malformed Release file?)

I know I have made a bo bo, but why, and how do I put it right?](*,) 

Thank you.

the converted.:-D[/B]

---

### Post by loclei on 2006-11-13
how do you connect to the internet?
and try this
```

sudo apt-get update

```
does it work?
and if it does try 
```

sudo apt-get install package

```
and if you are behing a proxy 
use this ```

export http_proxy="http://proxy:8080"
```

---

### Post by matt_tee on 2006-11-13
i tried the first solution and got this message :

Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-updates/Release](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/Release)  Unable to find expected entry  deb-src/binary-i386/Packages in Meta-index file (malformed Release file?)
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by matt_tee on 2006-11-13
the second :

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by matt_tee on 2006-11-13
i connect to the internet via a wireless g belkin modem, through a ntl cable modem.

---

### Post by Sef on 2006-11-13
Applications > Accessories > Terminal

then type

gksudo gedit /etc/apt/sources.list

then copy and paste your sources list here.

---

### Post by matt_tee on 2006-11-13
my internet connection works fine.

i was wondering how to delete :

[http://archive.ubuntu.com/ubuntu/dists/edgy-updates/Release:](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/Release:) Unable to find expected entry  deb-src/binary-i386/Packages in Meta-index file (malformed Release file?)

It is showing up in the error box, but not in the third party reposiory index, if it was, i would just delete from there.

where would it be on my system for a manual delete?

---

### Post by matt_tee on 2006-11-13
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://im.archive.ubuntu.com/ubuntu/](http://im.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://im.archive.ubuntu.com/ubuntu/](http://im.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://im.archive.ubuntu.com/ubuntu/](http://im.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://im.archive.ubuntu.com/ubuntu/](http://im.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

#AUTOMATIX REPOS START

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) dapper main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse

deb [http://easyubuntu.cafuego.net](http://easyubuntu.cafuego.net) main easyubuntu
#AUTOMATIX REPOS END
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed restricted main multiverse universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main


is that o.k?

---

### Post by argie on 2006-11-13
> **matt_tee said:**
> the second :

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

You should close synaptic before doing what loclei said, and only run one of those commands at a time.

---

### Post by matt_tee on 2006-11-13
also, in synaptic package manager, I have followed these instructions to extra repos, but I do not have a media tab. any ideas?

 How to apt-get the easy way (Synaptic)

    * Read #General Notes
    * System -> Administration -> Synaptic Package Manager
    * To enable the extra Universe and Multiverse repositories
         1. Settings -> Repositories
         2. In the Installation Media tab, click Add. There are three separate repositories; Dapper Drake, Security Updates and Updates. Select each repository and check Officially supported, Restricted copyright, Community maintained (Universe) and Non-free (Multiverse). Ensure you click OK between each repository to save your changes
         3. You should now see those three repositories under Channels. Make sure Officially supported, Restricted copyright, Community maintained (Universe) and Non-free (Multiverse) appears under each repository

---

### Post by matt_tee on 2006-11-13
did what you said but got this message:

Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package package

---

### Post by darrenm on 2006-11-13
Hello and well done for making a smart decision.

The entries in /etc/apt/sources.list need to be in the format:
```
deb http://archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse

```  - A deb or deb-src at the beginning, the URI in the middle and the trunks to use at the end.

Is it a Ubuntu repository you are trying to add or a 3rd party one?

---

### Post by matt_tee on 2006-11-13
i am sorry for troubling you, but can u guide me through the process. thanks.

i am new to this, but absolutely love it!

---

### Post by matt_tee on 2006-11-13
when you say 'trunks' at the end, is that rhyming slang?

trunks-shorts-backports?

---

### Post by matt_tee on 2006-11-13
i may have solved my problem, I have edited the source list, by deleting the old one and adding a whole new list.

this has solved the problem, thanks

---

### Post by darrenm on 2006-11-13
> **matt_tee said:**
> i may have solved my problem, I have edited the source list, by deleting the old one and adding a whole new list.

this has solved the problem, thanks

ok thats great. to avoid future problems I would clean up your repositories in synaptic.

Go into synaptic then settings then repositories and put the tick in all the boxes.

---

