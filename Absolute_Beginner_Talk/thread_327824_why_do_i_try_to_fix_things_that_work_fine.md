---
title: "why do i try to fix things that work fine"
date: 2006-12-29
forum: Absolute Beginner Talk
---

### Post by loserboy on 2006-12-29
ok.... well i went to synaptic to look for a lib, but when i searched nothing came up, so i went to repo settings, and where you can choose Main server or server for US mine was set to custom servers, I guess due to automatix or when i installed beryl.... anyway i changed it to main server thinking i could change back and i cant, now it seems like when i reload or check for updates its not checking as many places (used to be 73 now its 68)

so.... what did i do?

---

### Post by taurus on 2006-12-29
Let's have a look at your /etc/apt/sources.list then!!!

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by loserboy on 2006-12-30
here it is
> deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted

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
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

#AUTOMATIX REPOS START

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe multiverse
#AUTOMATIX REPOS END

deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main

deb [http://albertomilone.com/drivers/edgy/nonlegacy/32bit](http://albertomilone.com/drivers/edgy/nonlegacy/32bit) binary/


---

### Post by robenroute on 2006-12-30
It looks like Automatix has "taken over". But, no worries! Automatix should have made a backup of your original sources.list file. So, have a look in the /etc/apt directory and look for something that looks like sources.list_backup_...... You'll probably find your old repositories in there.

---

### Post by loserboy on 2006-12-30
well if automatix has taken over thats fine, i just wanna make sure im not missing any repos that i had before messed with it.

---

### Post by arnieboy on 2006-12-30
sources.list looks ok to me. Automatix added the missing official repos.
do a 
```
sudo apt-get update

```

---

