---
title: "Problem with libcairo2"
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by Xummoner on 2007-01-25
Hey guys, I can't remember exactly since when I've been having this "problem", actually more of an annoyance. What happens is that whenever I try to "sudo apt-get upgrade" I get the following message:
```
The following packages have been kept back:
  libcairo2 libcairo2-dev
```

I don't think those are actually important files for me since everything (well almost) is working great, but still I would like to know what repositories do I need to add to get those 2 files.
They might be related to beryl or kiba-dock, since they are the two things I can't manage to make work on my Dapper.

---

### Post by lamego on 2007-01-26
That message means that those packages are already installed, not that you need to install them. Those packages are from the main repos.

Could you post the remaining output from your error ?

---

### Post by Xummoner on 2007-01-26
This is what I get, is not that I think I don't have the packages, but they cannot be upgraded I guess.

```
david@David-Desktop:~$ sudo apt-get upgrade
Password:
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  libcairo2 libcairo2-dev
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
```

Oh, and I always get a message when I open Synaptic, that I have to upgrade those packages using the console or using the "Mark all upgrades" option, but it never works.

---

### Post by megamaced on 2007-01-26
I am having trouble updating libcairo2 as well. It's probably because I've been using unoffical repositories :D Serves me right I guess. Anyway, the problem lies with an incompatible version of libfreetype6.

```
$ sudo aptitude dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initialising package states... Done
Building tag database... Done
The following packages are BROKEN:
  libcairo2
1 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 229kB of archives. After unpacking 16.4kB will be freed.
The following packages have unmet dependencies:
  libcairo2: Depends: libfreetype6 (>= 2.2) but 2.1.10-1ubuntu2.2 is installed.
```

I've been using the Beryl repositories as well, so this leads me to believe they could be the source of the problem. I've also been using the Ubuntu 'Proposed' repo too. These are the unoffical repos I have set up:

```
deb http://gb.archive.ubuntu.com/ubuntu/ dapper-proposed main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper-proposed main restricted universe multiverse
deb http://download.tuxfamily.org/3v1deb dapper beryl-svn
deb-src http://download.tuxfamily.org/3v1deb dapper beryl-svn
deb http://ubuntu.beryl-project.org dapper main
deb http://www.albertomilone.com/drivers/dapper/latest/32bit binary/
```

---

### Post by megamaced on 2007-01-26
Okay, solved.

This...

```
deb http://ubuntu.beryl-project.org dapper main
```

... was the offending repository. Note that there are many mirrors that link to this. The 'beerorkid' repo is one of them. This repository never updates anymore so it's OK to remove it from your sources.list file. Once you've installed xserver-xgl then theres no need to keep this repo anyway. Plus it's only got Beryl 0.1.1 which is ancient. You should use the Beryl SVN repositories for Dapper now. Beryl is up to 0.2.0 :)

---

### Post by Xummoner on 2007-01-26
Oh thanks, I'll update my sources list. :)

---

