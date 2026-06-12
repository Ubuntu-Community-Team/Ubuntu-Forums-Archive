---
title: "[SOLVED] elusive packages..."
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by BenjaminDisraeli on 2007-12-25
hi, im quite new to ubuntu but i think i'm getting the hang of all this package management: except a few packages still elude me: mainly unrar (i've found unrar-free but no sign of the unfree version) and restricted-manager.

i've found a few posts from other users having similar problems, but they all seem to have been solved by ticking the universe /  multiverse repositories.

the following are the uncommented lines from sources.list

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

can anyone suggest that i am missing some repositories?  and possibly point me at them?

many thanks, and merry christmas

---

### Post by wormser on 2007-12-25
Now you need to update apt so it knows of the changes.

```
sudo apt-get update
```

---

### Post by LinuxIsInnovation on 2007-12-25
Looks like everything to me.. :)

---

### Post by BenjaminDisraeli on 2007-12-26
okay, so what simple mistake am I making...

disraeli@disraeli-laptop:~$ sudo apt-get update
Get: 1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Get: 2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper Release.gpg [189B]
Get: 3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get: 4 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports Release.gpg [191B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/multiverse Sources
Fetched 4B in 0s (5B/s)
Reading package lists... Done

disraeli@disraeli-laptop:~$ sudo apt-get install unrar
Reading package lists... Done
Building dependency tree... Done
Package unrar is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package unrar has no installation candidate

disraeli@disraeli-laptop:~$ sudo apt-get install restricted-manager
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package restricted-manager

---

### Post by chewearn on 2007-12-26
>  the following are the uncommented lines from sources.list

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
I don't have a dapper machine, so cannot test out for you.  But see here:
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=unrar&searchon=names&subword=1&version=dapper&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=unrar&searchon=names&subword=1&version=dapper&release=all)

Unrar package is in multiverse repository, which I believe you have not enable (no "dapper multiverse" in the above quote).

I suggest you check your repositories checkboxes in Synaptic.

---

### Post by BenjaminDisraeli on 2007-12-26
all my checkboxes in synaptic are checked, including the multiverse ones.

also, just to clarify, im running gutsy.
... this now makes me wonder why im using dapper repositories.

---

### Post by Cypher on 2007-12-26
When looking for packages, use the [http://packages.ubuntu.com](http://packages.ubuntu.com) site to track it down. You can see from this [link]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=unrar&searchon=names&subword=1&version=all&release=all") that the unrar (non-free) package is the Multiverse repo for all version of Ubuntu.

The fact that you are running Gutsy, but looking at the Dapper repos is slightly alarming, but it should STILL find unrar.

Did you do a upgrade from Dapper to Gutsy?

---

### Post by BenjaminDisraeli on 2007-12-26
nope, straight gutsy installation; right after i didn't update my symantec subscription and my windows OS got killed by a worm.

shouldn't be a problem with me just changing each of those lines to match the gutsy repositories should there?

anyway, thanks for the links: unfortunately brings me to a separate issue.
downloaded the unrar package for x86 and loaded it into the package installer to get an error: Dependency is not satisfiable: libc6.

according to synaptic i've got libc6 , libc6-dev and libc6-i686 all installed, also libcomfaceg1 and libcomfaceg1-dev. none of the rest of the packages look applicable.  correct me if im wrong?

---

### Post by BenjaminDisraeli on 2007-12-26
kindly ignore all of my problems, as it turns out: just because a CD says gutsy on it in nice blue pen, doesn't necessarily mean it's the gutsy distro.

many thanks for all your help, i wouldn't have noticed otherwise

---

