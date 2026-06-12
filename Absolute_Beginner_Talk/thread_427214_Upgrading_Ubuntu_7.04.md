---
title: "Upgrading Ubuntu 7.04"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by ECoder on 2007-04-29
Hello,

I'm trying to upgrade Ubuntu 6.10 to 7.04, I installed all the updates before I continue and press 'Upgrade' in the update-manager. A screen appears saying that the the upgrade-tool  is being downloaded, after that... the text: 'Preparing Upgrade' is bold, downloading packages. After a short while the following message appears:

Failed to fetch [http://nl.archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz](http://nl.archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz) Subproces gzip gaf de foutcode 1 terug

When I press 'Check' in the update-manager the same error appears. But I'm getting updates a lot of times automatically. What can I do to fix the error?

Peter.

---

### Post by Old Pink on 2007-04-29
```
sudo gedit sudo gedit /etc/apt/sources.list
```

Look for the [http://nl.archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz](http://nl.archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz) line and delete it. It's an edgy source, it's not needed to upgrade. :)

---

### Post by ECoder on 2007-04-29
Thanks for your answer. But I can't find the line in sources.list:

```

deb http://nl.archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://nl.archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://nl.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://nl.archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://nl.archive.ubuntu.com/ubuntu/ edgy universe
# deb-src http://nl.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://nl.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://nl.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe

#AUTOMATIX REPOS START

deb http://archive.canonical.com/ubuntu edgy-commercial main

deb http://wine.lowvoice.nl/apt edgy main

deb http://www.getautomatix.com/apt edgy main

deb http://archive.canonical.com/ubuntu dapper-commercial main

deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu edgy-updates universe multiverse

deb http://archive.ubuntu.com/ubuntu edgy-security main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu edgy universe multiverse
#AUTOMATIX REPOS END

```

---

### Post by Michaelt74 on 2007-04-29
I would recommend a fresh install of Ubuntu Feisty. There are lots of posts which report on problems with upgrades. Just my opinion.

---

### Post by ECoder on 2007-04-29
Hmm... I think I'll stick a little bit longer with 6.10. Working fine for me.

---

### Post by Michaelt74 on 2007-04-29
I've been using Feisty 7.04 for around a week now and find it a big improvement from Edgy. I liked Edgy but there were too many bugs & broken applications. Feisty is great!

Good luck

---

