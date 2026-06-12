---
title: "automatix2 problem"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by bengar on 2007-02-11
Hello people
Yesterday I was reinstalling dapper after a failure upgrading to edgy, Well the problem is after I installed automatix using the terminal, I make a mistake to load the automatix edgy 6.10 version,  I uninstalled it, and installed the automatix 6.06 dapper. Now the update available appear to upgrade automatix but is the edgy version, how I can avoid this? Tnks everybody

---

### Post by taurus on 2007-02-11
You probably need to edit /etc/apt/sources.list and make sure it says dapper instead of edgy in the entry for automatix.  If not sure, post your /etc/apt/sources.list here.

```
cat /etc/apt/sources.list
```

---

### Post by bengar on 2007-02-11
> **taurus said:**
> You probably need to edit /etc/apt/sources.list and make sure it says dapper instead of edgy in the entry for automatix.  If not sure, post your /etc/apt/sources.list here.

```
cat /etc/apt/sources.list
```

That is source my list...

> deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

#AUTOMATIX REPOS START

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) dapper main

# deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main

# deb [http://people.ubuntu.com/~seb128/deb](http://people.ubuntu.com/~seb128/deb) ./

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
#AUTOMATIX REPOS END

---

### Post by taurus on 2007-02-11
Edit your /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and remove this line from it.

```
deb http://www.getautomatix.com/apt edgy main
```
Save it.  Then run

```
sudo aptitude remove automatix2
sudo aptitude update
sudo aptitude install automatix2
```

---

### Post by bengar on 2007-02-11
Many thanks Taurus, all is running okay, I follow all the instructions, thank you very much for you attention.

---

