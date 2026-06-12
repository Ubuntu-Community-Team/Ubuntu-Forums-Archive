---
title: "is the kynaptic (package manager) down?"
date: 2005-07-06
forum: Absolute Beginner Talk
---

### Post by snoopgst on 2005-07-06
I have been trying to  install firefox and a few others.  I get this error: Some of the packages could not be retrieved from the server.

---

### Post by mtron on 2005-07-06
are you installing from the us repositories? i remember that there were some problems. 

Check your /etc/apt/sources.list and remove the us.

---

### Post by snoopgst on 2005-07-06
this is what my sources.list looks like: 

deb cdrom:[Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

---

### Post by ltmon on 2005-07-07
Yes you are.  I guess those servers (us.archive.ubuntu.com) are having some issues.

You can either wait for them to come back up, or use a different country.  

I'm in Australia so I use au.archive.ubuntu.com.  Maybe ca.archive.ubuntu.com (if it exists) will be faster from the US.  Change the relevant lines, click the "Update" button and try again.

L.

---

