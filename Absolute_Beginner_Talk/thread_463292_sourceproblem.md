---
title: "sourceproblem"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by Spacerman on 2007-06-03
hello.. I startet using ubuntu two days ago. and I don't have a clue to what I did wrong here....I think i deleted my source list and I have no backup.......anybody who knows how to fix this????

I get this when I open synaptic package control or whatever the name of it is....

E: Type ‘[ftp://ftp.domain.ext/path/to/repository’](ftp://ftp.domain.ext/path/to/repository’) is not known on line 22 in source list /etc/apt/sources.list
E: could not read source list.
Go to source directory to fix the problem.

---

### Post by taurus on 2007-06-03
There is something wrong with line 22 in your /etc/apt/sources.list.  So, you need to either fix it or remove it.

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by Spacerman on 2007-06-03
hmm.... but what am I supposed to do with that?
when I wrote this:
gksudo gedit /etc/apt/sources.list
this came up: 

## Major bug fix updates produced after the final release of the
## distribution.

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

[ftp://ftp.domain.ext/path/to/repository](ftp://ftp.domain.ext/path/to/repository) 


'/etc/apt/sources.list'
/etc/apt/sources.list
'sudo apt-get update'
'/etc/apt/sources.list'
app-install-data-commercial (5)

source
[ftp://ftp.domain.ext/path/to/repository](ftp://ftp.domain.ext/path/to/repository)
get source packagename


should I copy all this into my command line??? I tried than, and there were many bashes. 
permission denied.....all the way down..........

---

### Post by taurus on 2007-06-03
> **Spacerman said:**
> 
## Major bug fix updates produced after the final release of the
## distribution.

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

[ftp://ftp.domain.ext/path/to/repository](ftp://ftp.domain.ext/path/to/repository) 


'/etc/apt/sources.list'
/etc/apt/sources.list
'sudo apt-get update'
'/etc/apt/sources.list'
app-install-data-commercial (5)

source
[ftp://ftp.domain.ext/path/to/repository](ftp://ftp.domain.ext/path/to/repository)
get source packagename


Is that your /etc/apt/sources.list?  

There is something major screwed up if that is your /etc/apt/sources.list because your /etc/apt/sources.list should look something like this if you are running Feisty Fawn.

```

deb http://archive.ubuntu.com/ubuntu feisty main restricted
deb-src http://archive.ubuntu.com/ubuntu feisty main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu feisty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu feisty-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu feisty universe
deb-src http://archive.ubuntu.com/ubuntu feisty universe

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted

deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe

deb http://archive.ubuntu.com/ubuntu feisty multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty multiverse

deb http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu feisty-commercial main

```

---

### Post by Spacerman on 2007-06-03
Yeah, that's my sources list..... do you know how I can fix this without reinstalling ubuntu? something like setting the computer back to an earlier date or something like that?????

---

### Post by taurus on 2007-06-03
Which release are you running right now, Dappper, Edgy, or Feisty?  

Not sure how you manage to trash your /etc/apt/sources.list completely.

---

### Post by Spacerman on 2007-06-03
I'm running ubuntu 6.06 LTS......... I actually don't know how to find out what i'm running..... 6.06 LTS is what the cd-cover says.....

---

### Post by taurus on 2007-06-03
Okay, edit /etc/apt/sources.list again

```
gksudo gedit /etc/apt/sources.list
```
and remove everything in there.  Then, paste the following lines to it.

```

deb http://archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu dapper universe
deb-src http://archive.ubuntu.com/ubuntu dapper universe

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

deb http://archive.ubuntu.com/ubuntu dapper multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper multiverse

deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu dapper-commercial main

deb http://medibuntu.sos-sts.com/repo/ dapper free non-free
deb-src http://medibuntu.sos-sts.com/repo/ dapper free non-free 

```
Save it.  Then, from run

```
wget -q http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg -O- | sudo apt-key add -
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by Spacerman on 2007-06-03
Thanks man..... now it all works........

---

### Post by taurus on 2007-06-03
Just be real careful when you add something to /etc/apt/sources.list next time.

---

