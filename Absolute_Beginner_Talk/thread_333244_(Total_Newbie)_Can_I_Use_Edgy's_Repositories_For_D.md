---
title: "(Total Newbie) Can I Use Edgy's Repositories For Dapper ?"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by gidra on 2007-01-07
- Just installed Dapper and software is obviously outdated 

- Updated using Ubuntu updates but the software still ain't up to date eg. Firefox version 1.5

- Can I add edgy's repositories to sources.list in order to install  software ? Would they work correctly?

Thanks for any replies

---

### Post by Sasa_Ivanovic on 2007-01-07
Probably.
But a better solution would be to upgrade to Edgy.

---

### Post by gidra on 2007-01-07
- So each time a new ubuntu comes out I must do a fresh install in order to update software ?

- It would be kind of you if you can post me a copy of the contents of edgy's sources.list

---

### Post by Sasa_Ivanovic on 2007-01-07
yeah sure
```


deb http://mk.archive.ubuntu.com/ubuntu/ edgy main restricted multiverse universe
deb-src http://mk.archive.ubuntu.com/ubuntu/ edgy main restricted multiverse universe

## Major bug fix updates produced after the final release of the
## distribution.
deb http://mk.archive.ubuntu.com/ubuntu/ edgy-updates main restricted multiverse universe
deb-src http://mk.archive.ubuntu.com/ubuntu/ edgy-updates main restricted multiverse universe

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://mk.archive.ubuntu.com/ubuntu/ edgy universe
# deb-src http://mk.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://mk.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://mk.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted multiverse universe
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted multiverse universe
# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe

```

---

### Post by gidra on 2007-01-07
Thanks Sasa_Ivanovic

---

### Post by gidra on 2007-01-07
- Added Edgy's repositories to Dapper's sources.list
- sudo apt-get update
- Gives me some error i.e. they're incompatible
- Guess I have to find another way to automatically update software

---

### Post by wally83 on 2007-01-07
> **gidra said:**
> - So each time a new ubuntu comes out I must do a fresh install in order to update software ?


No no.

You can also upgrade your current Dapper system to Edgy. There is now even an update manager for doing so:

open terminal and type:
```
gksu &#8220;update-manager -c -d&#8221;
```

More info: [http://www.howtogeek.com/howto/ubuntu/upgrading-ubuntu-from-dapper-to-edgy-with-update-manager/](http://www.howtogeek.com/howto/ubuntu/upgrading-ubuntu-from-dapper-to-edgy-with-update-manager/)

---

### Post by gidra on 2007-01-07
Cheers, upgrade started. I had to do some configuration with my soundcard (HDA INTEL ALC880) and installed some themes. Hope those won't be affecte with the upgrade

---

