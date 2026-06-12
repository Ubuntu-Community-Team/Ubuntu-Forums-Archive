---
title: "deb' is not known on line 77 in source list"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by Ginge.Ghana on 2007-12-10
hee, im just new to ubuntu and so i tried to install some programs but now every time when i try to open synaptic package manager it gives me this error: 
E: Type '\u201cdeb' is not known on line 77 in source list /etc/apt/sources.list
E: The list of sources could not be read.
:S and i have no clue what to do :confused:
can someone please help me?

---

### Post by PriceChild on 2007-12-11
*moves approves and bumps*

You have a line in the /etc/apt/sources.list that shouldn't be there.

Could you paste the file please? (output of ```
cat /etc/apt/sources.list
``` in terminal)

---

### Post by mcduck on 2007-12-11
> **PriceChild said:**
> *moves approves and bumps*

You have a line in the /etc/apt/sources.list that shouldn't be there.

Could you paste the file please? (output of ```
cat /etc/X11/xorg.conf
``` in terminal)

What PriceChild means is could you post the output of ```
cat /etc/apt/sources.list
```

---

### Post by PriceChild on 2007-12-11
gah I always get those two mixed up without noticing because they're so often messed with... thanks mcduck *fixes*

---

### Post by Ginge.Ghana on 2007-12-11
here you go:P
thanx btw for replying!!

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://gh.archive.ubuntu.com/ubuntu/](http://gh.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://gh.archive.ubuntu.com/ubuntu/](http://gh.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://gh.archive.ubuntu.com/ubuntu/](http://gh.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://gh.archive.ubuntu.com/ubuntu/](http://gh.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://gh.archive.ubuntu.com/ubuntu/](http://gh.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://gh.archive.ubuntu.com/ubuntu/](http://gh.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://gh.archive.ubuntu.com/ubuntu/](http://gh.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://gh.archive.ubuntu.com/ubuntu/](http://gh.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://gh.archive.ubuntu.com/ubuntu/](http://gh.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://gh.archive.ubuntu.com/ubuntu/](http://gh.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://gh.archive.ubuntu.com/ubuntu/](http://gh.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://gh.archive.ubuntu.com/ubuntu/](http://gh.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gh.archive.ubuntu.com/ubuntu/](http://gh.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://gh.archive.ubuntu.com/ubuntu/](http://gh.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) gutsy main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy multiverse universe
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) gutsy main
“deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main”

---

### Post by skymera on 2007-12-11
wow, all your sources seem to not be in use.

take the # sign away from all the lines beginning with **deb**

and the very last line has a " before deb, simple remove

---

### Post by Ginge.Ghana on 2007-12-11
sorry but how do i take all the # away and the ''
do i still use the terminalal?
thanx for your quick reply:D

---

### Post by mcduck on 2007-12-11
You can run 'gksudo gedit /etc/apt/sources.lst' to open the file for editing with Gedit.

Edit. While you are at it, you should probably just remove the last line completely. It's for Automatix Edgy repository, not for Gutsy. (And next time I'd recommend staying away from Automatix, it's not needed for anything any more and often causes more trouble than it's worth..)

This is how the file should look like:
```
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gh.archive.ubuntu.com/ubuntu/ gutsy main restricted
# deb-src http://gh.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gh.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# deb-src http://gh.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gh.archive.ubuntu.com/ubuntu/ gutsy universe
# deb-src http://gh.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://gh.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# deb-src http://gh.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gh.archive.ubuntu.com/ubuntu/ gutsy multiverse
# deb-src http://gh.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://gh.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# deb-src http://gh.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gh.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://gh.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
# deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb http://www.getautomatix.com/apt gutsy main
deb http://archive.ubuntu.com/ubuntu/ gutsy multiverse universe
deb http://www.getautomatix.com/apt gutsy main
```

---

### Post by skymera on 2007-12-11
o sorry should have said

gksudo gedit /etc/apt/sources.list
in the termynal

then just take the # away from ONLY the lines beginning weith DEB

and take away the " sign too :lol:

---

### Post by Ginge.Ghana on 2007-12-11
srry but how do i replace it with the old list... it doesn't give me the permission to replace it... i feel stupid:P with windows i never have problems like this.

---

### Post by mcduck on 2007-12-11
> **Ginge.Ghana said:**
> srry but how do i replace it with the old list... it doesn't give me the permission to replace it... i feel stupid:P with windows i never have problems like this.

Like we have already said, run 'gksudo gedit /etc/apt/sources.lst' to open the file for editing as root user.

---

