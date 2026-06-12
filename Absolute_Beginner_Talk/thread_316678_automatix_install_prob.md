---
title: "automatix install prob"
date: 2006-12-11
forum: Absolute Beginner Talk
---

### Post by Doug11 on 2006-12-11
I get this error when im almost through instaling automatix. It seem debian is not in the repos. How can I add it and what do i have to do to do it.



E: Type '“deb' is not known on line 34 in source list /etc/apt/sources.list
E: The list of sources could not be read.

---

### Post by tchoklat on 2006-12-11
it looks like your line 34 in the sources.list is incorrect can you post it

---

### Post by Doug11 on 2006-12-11
This is what i get when i do a gedit /etc/apt.list
Should I un-comment them?




deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy universe
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

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
“deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main”
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

---

### Post by arnieboy on 2006-12-11
delete the following line from sources.list:
“deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main”
and do a
```
sudo apt-get update
```

---

