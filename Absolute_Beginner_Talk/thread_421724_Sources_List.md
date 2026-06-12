---
title: "Sources List"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by ziffnabb on 2007-04-24
Hi:
I upgraded from Edgy to Feisty.  I had a problem in that the download part would stop with a connection refused error.  When I tried again, I got an error that line 2 in my sources list was malformed.  I ended up having to comment out a few lines to get update manager to run.

Now when I try to enable third party repositories, I get the same error.  This is my sources file.  Would anyone be able to tell me what is wrong and how to fix it?

Thanks,
Ziffnabb


# deb None edgy main restricted
# deb-src None edgy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
## deb None edgy-updates main restricted
# deb-src None edgy-updates restricted main multiverse universe #Added by software-properties

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty universe
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-security main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-security restricted main multiverse universe #Added by software-properties
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

#AUTOMATIX REPOS START

# deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

# deb None edgy-backports main restricted universe multiverse

# deb None edgy-updates universe multiverse

# deb None edgy-security main restricted universe multiverse

# deb None edgy universe multiverse
#AUTOMATIX REPOS END

## Avant Window Navigator
# deb [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) edgy avant-window-navigator
# deb-src [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) edgy avant-window-navigator
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty main multiverse restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty universe main multiverse restricted #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates universe main multiverse restricted

---

### Post by zvacet on 2007-04-24
Change your Edgy repos to Feisty

```
 sudo sed -e 's/\sedgy/ feisty/g' -i /etc/apt/sources.list 
```

and uncomment all commented lines.if you don´t have luck with it replace source list with

[http://easylinux.info/wiki/Ubuntu:Feisty#How_to_add_extra_repositories]("http://easylinux.info/wiki/Ubuntu:Feisty#How_to_add_extra_repositories")

---

### Post by ziffnabb on 2007-04-24
Hi zvacet.

I used the link you provided.  That seemed to do the trick.

Thanks,
Ziffnabb

---

