---
title: "I can't use apt-get plz help"
date: 2006-10-23
forum: Absolute Beginner Talk
---

### Post by D_frag on 2006-10-23
Please i really need help in this issue 
I've been trying to use apt-get and  it's not working because there are broken dependecies 
```
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libc6: Depends: tzdata but it is not installable
  libc6-dev: Depends: libc6 (= 2.3.6-0ubuntu20) but 2.3.6.ds1-6 is to be installed
  libc6-i386: Depends: libc6 (= 2.3.6-0ubuntu20) but 2.3.6.ds1-6 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

and this is what i get when i type apt-get -f install
```

Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
  libc6: Depends: tzdata but it is not installable
  libc6-dev: Depends: libc6 (= 2.3.6-0ubuntu20) but 2.3.6.ds1-6 is installed
  libc6-i386: Depends: libc6 (= 2.3.6-0ubuntu20) but 2.3.6.ds1-6 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies


```
The Tzdata package is not available in synaptic and the repos are enabled so i tried downloading a .deb file from here 
[http://packages.debian.org/unstable/libs/tzdata](http://packages.debian.org/unstable/libs/tzdata)

when i tried installing i got this error
```

dpkg: error processing tzdata_2006m-1_all.deb (--install):
 trying to overwrite `/usr/share/zoneinfo/zone.tab', which is also in package locales
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 tzdata_2006m-1_all.deb

```

and now i can't use apt-get at all i have a problem with mplayer and i am tryig to remove it using apt-get i cant !!
it says i have to resolve this error , please help!

---

### Post by grim918 on 2006-10-23
Has apt-get ever worked for you or did this problem come about after you made some changes. You should do some back track thinking to see what might have caused the problem.

You might want to try reinstalling Apt since you say that apt-get is no longer working. Here is a link to a similar thread: [http://ubuntuforums.org/showthread.php?t=238367](http://ubuntuforums.org/showthread.php?t=238367)

---

### Post by taurus on 2006-10-23
Don't forget to run update first before you upgrade or install anything!

```

sudo aptitude update
sudo aptitude upgrade

```

---

### Post by TheWizzard on 2006-10-23
are you on dapper or edgy? 

how did you get this message (what did you type?): 
> Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libc6: Depends: tzdata but it is not installable
  libc6-dev: Depends: libc6 (= 2.3.6-0ubuntu20) but 2.3.6.ds1-6 is to be installed
  libc6-i386: Depends: libc6 (= 2.3.6-0ubuntu20) but 2.3.6.ds1-6 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
if tzdata is not in the repo's ???

besides, why do you want to install tzdata? i don't think you need it.

---

### Post by az on 2006-10-23
Debian and Ubuntu are not binary-compatible.

You broke your package manager by mixing Debian and Ubuntu repositories.

Reenable the debian repos and dist-upgrade to fix the conflict.  Live with what you get.

---

### Post by D_frag on 2006-10-26
> **azz said:**
> Debian and Ubuntu are not binary-compatible.

You broke your package manager by mixing Debian and Ubuntu repositories.

Reenable the debian repos and dist-upgrade to fix the conflict.  Live with what you get.

I dont think i had the debian repos enabeled in the first place ?! but maybe if i enable them things would work if you would just tell me how ? i mean whats the address and if there is a key ?

---

### Post by az on 2006-10-27
Apt is telling you that libc6 version 2.3.6.ds1-6 is not completely installed.  That is a version from Debian Unstable.

Either completely upgrade your libc6 to that version or try to manually reinstall the libc6 version from Ubuntu.

---

