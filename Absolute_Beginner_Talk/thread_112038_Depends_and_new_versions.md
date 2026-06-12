---
title: "Depends and new versions"
date: 2006-01-03
forum: Absolute Beginner Talk
---

### Post by schucki.be on 2006-01-03
Hello, 
I am quite new to Linux and this community thing, so i hope that i am posting it the right way...

I try to install Mplayer and mythtv. When i do an apt -get install mplayer-586 i get :

Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mplayer-586: Depends: libfribidi0 (>= 0.10.5-4) but 0.10.5-2 is to be installed
               Depends: libgcc1 (>= 1:4.0.2) but 1:4.0.1-4ubuntu9 is to be installed
               Depends: libjack0.100.0-0 (>= 0.100.0) but it is not installable
               Depends: libstdc++6 (>= 4.0.2-3) but 4.0.1-4ubuntu9 is to be installed
E: Broken packages

And when I look in the SPM i only find the older versions (eg libstc++6 version 4.0.1-4). I think i have the correct repos, checked that 1000 times with examples in threads...

What's wrong ?:( 
I am desperate installing all day, tried everything again, but still having this errors...

Thnx,
schucki.be

---

### Post by MartinJ on 2006-01-03
I don't have mplayer-586 in my repositories list so can't really help you completely.  Have you tried mplayer-386?  Works ok here.

---

### Post by schucki.be on 2006-01-03
[QUOTE=MartinJ]I don't have mplayer-586 in my repositories list so can't really help you completely.  Have you tried mplayer-386?  Works ok here.[/QUOTE]

Thnx MartinJ,
The 386 version is also not installing ...:(

---

### Post by jimrz on 2006-01-04
I see both mplayer-586 and -386 in Synaptic. Both are in multiverse, what repo list are you using?  Here is mine:

#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

## Uncomment the following two lines to fetch updated software from the network
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse universe main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe main restricted multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

## http 100mbit/s mirror provided thanks to OVH [http://ovh.com](http://ovh.com)
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free

---

### Post by schucki.be on 2006-01-05
Thnx Jimrz,
I fixed it yesterday, but forgot to edit my message...:oops: 
I found another source.list, used it and voila.
This .list looks kinda the same as the one i had, at least at first glance...
I have to check the diffs so i can learn from this.
I'll post the diffs so maybe anybody else can benefit.

Thnx again,

Schucki.be

---

