---
title: "sources list for serer 7.10"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by Station on 2008-03-07
can someone post me there sources list for their server. ubuntu server edition 7.10

I seem to be having a 
Err [http://ca.archive.ubunto.com](http://ca.archive.ubunto.com) gutsy/multiverse Translation-en_CA
"Temporary failure resolving 'security.ubuntu.com'"

She won't finish upgrade or update

---

### Post by some_random_noob on 2008-03-07
I'm actually running Kubuntu 7.10 (Non-server) but you should be able to modify the following and pluck the bits you want. Unfortunately, many of my ones point to a NZ server:

```
# 
# deb cdrom:[Kubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.2)]/ gutsy main restricted

# deb cdrom:[Kubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.2)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://nz.archive.ubuntu.com/ubuntu/ gutsy main
deb-src http://nz.archive.ubuntu.com/ubuntu/ gutsy main

## Major bug fix updates produced after the final release of the
## distribution.
deb http://nz.archive.ubuntu.com/ubuntu/ gutsy-updates main
deb-src http://nz.archive.ubuntu.com/ubuntu/ gutsy-updates main

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://nz.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://nz.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://nz.archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://nz.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://nz.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://nz.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://nz.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://nz.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://nz.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://nz.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu gutsy-security main
deb-src http://security.ubuntu.com/ubuntu gutsy-security main
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

```

---

### Post by Station on 2008-03-07
so if i am having problems connecting and updating. I could just change the country code in the source list?

thanks

---

### Post by kesman on 2008-03-07
> **Station said:**
> can someone post me there sources list for their server. ubuntu server edition 7.10

I seem to be having a 
Err [http://ca.archive.ubunto.com](http://ca.archive.ubunto.com) gutsy/multiverse Translation-en_CA
"Temporary failure resolving 'security.ubuntu.com'"

She won't finish upgrade or update

Well first of all, it's Ubuntu, not Ubunto, and second, if there's failure in security.ubuntu.com then the problem is not in that line you mentioned.

---

### Post by Station on 2008-03-07
> **kesman said:**
> Well first of all, it's Ubuntu, not Ubunto, and second, if there's failure in security.ubuntu.com then the problem is not in that line you mentioned.

A simple typing error that isn't in the sources.list. 

Are you saying that the problem doesn't lie within /apt/sources file then?

---

### Post by Nythain on 2008-03-07
if that typo isnt actually contained in your sources.list then you could try changing your country code, or removing the country code all together, but that might or might not fix your problem... what does your sources.list file look like

---

### Post by Station on 2008-03-08
#
# deb cdrom:[Ubuntu-Server 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted

#deb cdrom:[Ubuntu-Server 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

What I don't understand is why I get the 
Temporary failure resolving 'ca.archive.ubuntu.com'

All I am trying to do is update

---

