---
title: "Feisty auto update error"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by luvinit on 2007-04-27
HI, I am trying the auto update to Feisty, but it fails to fetch file 133, giving the error

Failed to fetch [http://packages.freecontrib.org/plf/dists/dapper/Release.gpg](http://packages.freecontrib.org/plf/dists/dapper/Release.gpg) Could not connect to packages.freecontrib.org:80 (88.191.33.6), connection timed out
Failed to fetch [http://packages.freecontrib.org/plf/dists/dapper/free/i18n/Translation-en_GB.bz2](http://packages.freecontrib.org/plf/dists/dapper/free/i18n/Translation-en_GB.bz2) Could not connect to packages.freecontrib.org:80 (88.191.33.6), connection timed out
Failed to fetch [http://packages.freecontrib.org/plf/dists/dapper/non-free/i18n/Translation-en_GB.bz2](http://packages.freecontrib.org/plf/dists/dapper/non-free/i18n/Translation-en_GB.bz2) Could not connect to packages.freecontrib.org:80 (88.191.33.6), connection timed out
Failed to fetch [http://lt.k1011.nutime.de/repository/dists/edgy/main/binary-i386/Packages.gz](http://lt.k1011.nutime.de/repository/dists/edgy/main/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://ubuntu.geole.info/dists/dapper/universe/binary-i386/Packages.gz](http://ubuntu.geole.info/dists/dapper/universe/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://ubuntu.geole.info/dists/dapper/multiverse/binary-i386/Packages.gz](http://ubuntu.geole.info/dists/dapper/multiverse/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://ubuntu.geole.info/dists/edgy/universe/binary-i386/Packages.gz](http://ubuntu.geole.info/dists/edgy/universe/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://ubuntu.geole.info/dists/edgy/multiverse/binary-i386/Packages.gz](http://ubuntu.geole.info/dists/edgy/multiverse/binary-i386/Packages.gz) 404 Not Found

it says this is usually some sort of network problem Is it maybe sources list based?

Thanks. Mark.

---

### Post by Cypher on 2007-04-27
Wow, you just have all sorts of wonderful stuff in your sources.list file huh?

Could you tell us what
```

cat /etc/apt/sources.list

```
shows you..

---

### Post by luvinit on 2007-04-27
Erm, thanks, I'll take that as a compliment! Here it is:

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy main restricted multiverse universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy main restricted multiverse universe

## Add comments (##) in front of any line to remove it from being checked.

## Use the following sources.list at your own risk.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
    
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)

deb [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free

deb-src [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu

## servers. RealPlayer10, Opera and more to come.)

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

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
deb [http://www.geexbox.org/debian/](http://www.geexbox.org/debian/) unstable main
deb-src [http://www.geexbox.org/debian/](http://www.geexbox.org/debian/) unstable main

deb [http://ubuntu.geole.info/](http://ubuntu.geole.info/) dapper universe multiverse
deb [http://ubuntu.geole.info/](http://ubuntu.geole.info/) edgy universe multiverse
deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main
#afterXleep Aptana Repository
deb [http://ubuntu.mylemontree.com/packages/](http://ubuntu.mylemontree.com/packages/) aptana-beta/
deb [http://lt.k1011.nutime.de/repository](http://lt.k1011.nutime.de/repository) edgy main

While we're at it, is it actually safe to upgrade or will it just mean taking a week to fix everything?

---

### Post by compmodder26 on 2007-04-27
First off, it is very unwise to mix distributions in your repository list.  You have lines for Dapper and Edgy both.  Second, when you upgrade to feisty, you want to comment all 3rd party repositories.  The upgrade will not like them and will most likely cause problems, perhaps even hose your installation.  If the address of the repository doesn't include "ubuntu.com", you should comment it, with the except of the Backports repositories, they are from "ubuntu.com" but they should also be commented.

---

### Post by Cypher on 2007-04-27
OK, now for the next big question. Which version of Ubuntu are you using? Dapper or Edgy?? You should, in general, only keep the repos for the version you're using. There is no reason to have both of them.

Beyond that though, I think you're problem is VERY easy to fix. Right from this post, try to access the "ubuntu.geole.info", "it.k1011.nutime.de/reposity" and the "packages.freecontrib.org/plf" locations and you'll get the same errors that Synaptic is reporting.

So just add a "#" in front of all of these offending repositories and you should be back in business..

If you need programs from these specific repos, the author has moved them somewhere else, so get the new addresses for it..

---

### Post by luvinit on 2007-04-27
OK, I will get onto commenting out those lines. I am using Edgy, the dapper lines are most likely there from not having a clue what I was doing when I first started, plus maybe a willingness to experiment. Thanks.

---

### Post by Cypher on 2007-04-27
Experimentation is good, and in general unless you explicitely say to use the Dapper repos, Apt-get/Synaptic/aptitude is pulling files from the Edgy repos anyway..

---

### Post by luvinit on 2007-04-27
OK, I did the upgrade, against my better judgement  :lolflag: and now on boot it pauses for a cuple of minutes then gives the following message:

can't access tty, job control turned off

any ideas what I can do?

---

