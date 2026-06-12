---
title: "update duplicates issue"
date: 2013-12-11
forum: Any Other OS
---

### Post by manuleka on 2013-12-11
platform: Elementary OS Luna (Ubuntu 12.04)

i'm still a novice in linux but have noticed when i run update i get this:
```

Reading package lists... Done
W: Duplicate sources.list entry http://security.ubuntu.com/ubuntu/ precise-security/restricted amd64 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_restricted_binary-amd64_Packages)
W: Duplicate sources.list entry http://security.ubuntu.com/ubuntu/ precise-security/main amd64 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://security.ubuntu.com/ubuntu/ precise-security/multiverse amd64 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_multiverse_binary-amd64_Packages)
W: Duplicate sources.list entry http://security.ubuntu.com/ubuntu/ precise-security/universe amd64 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_universe_binary-amd64_Packages)
W: Duplicate sources.list entry http://security.ubuntu.com/ubuntu/ precise-security/restricted i386 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_restricted_binary-i386_Packages)
W: Duplicate sources.list entry http://security.ubuntu.com/ubuntu/ precise-security/main i386 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_main_binary-i386_Packages)
W: Duplicate sources.list entry http://security.ubuntu.com/ubuntu/ precise-security/multiverse i386 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry http://security.ubuntu.com/ubuntu/ precise-security/universe i386 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_universe_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

```

here's my source.list
```

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to

# newer versions of the distribution.
deb http://nz.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://nz.archive.ubuntu.com/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://nz.archive.ubuntu.com/ubuntu/ precise-updates restricted main
deb-src http://nz.archive.ubuntu.com/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://nz.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://nz.archive.ubuntu.com/ubuntu/ precise universe
deb http://nz.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://nz.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://nz.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://nz.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://nz.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://nz.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://nz.archive.ubuntu.com/ubuntu/ precise-backports restricted main multiverse universe
deb-src http://nz.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner
deb-src http://archive.canonical.com/ubuntu precise partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb http://extras.ubuntu.com/ubuntu precise main
# deb-src http://extras.ubuntu.com/ubuntu precise main
deb http://security.ubuntu.com/ubuntu/ precise-security restricted main multiverse universe

```

i don't really understand where the duplicates its referring to can some one help please?

cheers

---

### Post by Bashing-om on 2013-12-11
manuleka; Hi !

Sure, help is what we do !
I see this:
> 
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security restricted main multiverse universe
 in your sources list file as a duplicate of this stanza:
> 
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse


Remove or comment out that last offending line, and all should be good. Standard operating procedure -> make copy of file prior to any editing !

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by manuleka on 2013-12-11
thank you that fixed it :)

---

### Post by Bashing-om on 2013-12-11
manuleka; Hey,

You are welcome. Great you have resolution.

ubuntu
[INDENT][INDENT]all for one and 1 for all
[/INDENT][/INDENT]

---

