---
title: "Why does this happen ?"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by burt_57 on 2007-07-11
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.:confused:

---

### Post by dannyboy79 on 2007-07-11
please post the output from this command, than I can help

cat /etc/apt/sources.list

also, did you do a
sudo aptitude update && sudo apt-get update
first?

---

### Post by dreadlord_chris on 2007-07-11
That just happens sometimes - could be a lot of things. As long as it's not all your repositories or happens all the time, there's nothing to worry about...

---

### Post by dreadlord_chris on 2007-07-11
> **dannyboy79 said:**
> 
also, did you do a
sudo aptitude update && sudo apt-get update
first?

uhm... those commands both do the same thing....

---

### Post by burt_57 on 2007-07-11
> **dannyboy79 said:**
> please post the output from this command, than I can help

cat /etc/apt/sources.list

also, did you do a
sudo aptitude update && sudo apt-get update
first?

robert@robert-desktop:~$ cat /etc/apt/sources.list
## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty restricted main multiverse universe #Added by software-properties

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates main restricted #Added by software-properties

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security restricted main universe #Added by software-properties

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse #Added by software-properties

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-proposed restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-proposed restricted main multiverse universe #Added by software-properties
robert@robert-desktop:~$

---

### Post by burt_57 on 2007-07-11
> **dreadlord_chris said:**
> uhm... those commands both do the same thing....

It get stuck at 99%, hum why I wonder

Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Packages           
99% [Connecting to security.ubuntu.com (82.211.81.138)]                                                                                                     
99% [Waiting for headers]

---

### Post by dannyboy79 on 2007-07-11
> **dreadlord_chris said:**
> uhm... those commands both do the same thing....
um, they are in theory suppose to BUT I have seen problems with mediabuntu repo's where I had to use apt-get update versus aptitude update for it to work so I merely informed him of that.

---

### Post by dannyboy79 on 2007-07-11
you can always try to change the location of the servers you connect to. it's done thru synaptic, I am not home right now so I can't tell you for sure but it's within the edit, preferences I beleive, then you can pick a different server to get your updates from and then it'll update your entire sources.list to the new location servers. I believe this will only work for any servers that are REAL trusted Ubuntu repo's though.

---

### Post by burt_57 on 2007-07-11
Thank, done and done

---

