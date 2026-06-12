---
title: "kdelibs4 version is out of sync with kdelibs4-dev"
date: 2005-10-10
forum: Bug Reports / Support
---

### Post by offby1 on 2005-10-10
Actual command:
```
sudo apt-get install -f kdelibs4-dev
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
  kdelibs4-dev: Depends: kdelibs4 (= 4:3.4.0-0ubuntu3.4) but 4:3.4.2-0ubuntu0hoary2 is to be installed
                Depends: kdelibs-bin (= 4:3.4.0-0ubuntu3.4) but 4:3.4.2-0ubuntu0hoary2 is to be installed
E: Broken packages

```
/etc/apt/sources.list:
```

#deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb http://ca.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ca.archive.ubuntu.com/ubuntu hoary universe multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu hoary universe multiverse

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu hoary-backports main restricted universe multiverse

```

---

