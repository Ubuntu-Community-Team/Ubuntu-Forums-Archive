---
title: "Wine July where?"
date: 2005-07-29
forum: Bug Reports / Support
---

### Post by strikeforce on 2005-07-29
I just got home today and I can see that the July version has shifted it.  I can't find it the only version I can find is 20050419 The july version isn't there.  Am I looking in the wrong place?

My sources.list is as follows.
```

marc@ubuntu:~/folding$ sudo cat /etc/apt/sources.list
## Uncomment the following two lines to fetch updated software from the network
deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://au.archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://au.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://au.archive.ubuntu.com/ubuntu hoary universe
deb-src http://au.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

## Backports
#deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
#deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted

deb http://mirror.brianpuccio.net/ubuntu-backports-repository/ hoary-backports main universe multiverse restricted
deb http://mirror.brianpuccio.net/ubuntu-backports-repository/ hoary-extras main universe multiverse restricted
deb http://archive.ubuntu.com/ubuntu hoary-backports main universe multiverse restricted

```

---

### Post by Juergen on 2005-07-29
It seems not even to be in Breezy so far, so you can't have a backport of it.

But the winers build a package, look here:
[http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb)

---

