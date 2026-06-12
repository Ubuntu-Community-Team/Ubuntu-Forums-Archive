---
title: "error going from edgy to feisty"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by Happy_Man on 2007-04-17
Hey everyone,

I decided to beat the server slowdown that will inevitably occur come release, by upgrading my system today! Unfortunately, it won't let me. I went ahead and typed in 

```

update-manager -d

```

and it showed up, and I clicked the upgrade button. So far so good. Then it gets to the second step, and throws this error:

> 
Failed to fetch [http://archive.canonical.com/ubuntu/dists/feisty-commercial/main/binary-i386/Packages.bz2](http://archive.canonical.com/ubuntu/dists/feisty-commercial/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://archive.canonical.com/ubuntu/dists/feisty-commercial/main/binary-i386/Packages.bz2](http://archive.canonical.com/ubuntu/dists/feisty-commercial/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)


It then "restores my system to its original state" and exits the upgrader. I've tried three times. Same error, same place. What should I do?

---

### Post by onon_onon on 2007-04-17
I'm upgrading right now, and everything is going fine with the repositories.

---

### Post by Seisen on 2007-04-17
Whats it look like in your source list. Post what it says for that repo.

```
sudo gedit /etc/apt/sources.list
```

---

### Post by old_geekster on 2007-04-17
I did two separate upgrades from Edgy to Feisty using this command:

sudo update-manager -c -d

Both worked without making any changes to the sources list.

---

### Post by RomeReactor on 2007-04-17
Hi. I've read here and there that some people are having trouble upgrading this way; another option is to download the [Feisty alternate cd]("http://mirrors.easynews.com/linux/ubuntu-releases/feisty/") and add it to the repositories: With the alternate cd in the tray, open Synaptic, go to "Settings-->Repositories", click on the middle tab (Third Party) and click on **Add Cdrom**; Reload the package information (press **Reload** on the top left) and you're good to go.

Please note that I myself haven't upgraded, so I have no experience with the effectiveness of this method; however, I've read that this works for many people having trouble upgrading by downloading the packages directly from the servers.

---

### Post by Happy_Man on 2007-04-18
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates restricted main multiverse universe #Added by software-properties

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security restricted main multiverse universe #Added by software-properties
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

#AUTOMATIX REPOS START

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse #Added by software-properties

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates universe multiverse #Added by software-properties

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse #Added by software-properties

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy universe multiverse #Added by software-properties
#AUTOMATIX REPOS END

deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy main

deb [http://www.albertomilone.com/drivers/edgy/newlegacy/32bit](http://www.albertomilone.com/drivers/edgy/newlegacy/32bit) binary/

deb [http://flomertens.free.fr/ubuntu/](http://flomertens.free.fr/ubuntu/) edgy main main-all

deb [http://debian.websterwood.com/](http://debian.websterwood.com/) edgy main
deb-src [http://debian.websterwood.com/](http://debian.websterwood.com/) edgy main

---

### Post by bravemosquito on 2007-04-18
You must change **edgy** word with **feisty** to work

---

### Post by Seisen on 2007-04-18
Thats the way I've always done it and have had no problems with it. I know it might sound tedious but hey if it works it  works.

---

### Post by Happy_Man on 2007-04-18
Bump

---

