---
title: "[SOLVED] repeated md5 mismatch"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by revealer on 2007-07-01
***SOLVED***
i read some similar cases and they're resolved by changing the mirror
i switched from my country to usa and it worked
thanks anyway


i recently reinstalled my system and i'm trying to download the updates...
however, there's a package called linux-restricted-modules-generic that gives me an md5 mismatch every time i try to install it :s
it's a shame 'cause i also need this to install nvidia drivers
is there an alternative way of getting this package??
maybe a .deb package?

---

### Post by limbourg31 on 2007-07-01
try and install through the restricted drivers utility or Easyubuntu

---

### Post by revealer on 2007-07-01
tried with automatix2 and had same result
an apt-get error
the restricted drivers manager needs the linux-restricted-modules-generic to run

---

### Post by limbourg31 on 2007-07-01
try an apt-get remove of everything, and then an adept fix-broken packages or dependencies, try apt-get after that for the linux-resricted-modules-generic

---

### Post by bodhi.zazen on 2007-07-01
It is best to wait a few hours/days until the md5 mismatch resolves itself.

Otherwise file a bug report. 

Removing and re-installing packages will not resolve the issue.

---

### Post by revealer on 2007-07-01
i tried downloading the .deb package with firefox from security.ubuntu.com's pool and it seems it's corrupted, maybe this is the reason.
it's strange because i installed this package with no problems in my last instalation
thaks anyway

---

### Post by revealer on 2007-07-01
i checked the .deb and it has 2 compressed  tarballs inside.
one of them (data.tar.gz) is corrupted
:S

---

### Post by limbourg31 on 2007-07-01
it might be the way the package installed itself, mayble broken downloads, whcih corrupted the md5, but bodhi.zahen and revealer are right when saying the package may be corrupted itself

---

### Post by revealer on 2007-07-03
> It is best to wait a few hours/days until the md5 mismatch resolves itself.

I followed bohdi.zazen's advice but it didn't give me results.
I'll submit the bug (if it's really a bug and no error from my part) but I'd be glad if someone helps me because i can't get beryl nor nvidia drivers without this package
Before i reinstalled i had both beryl, nvidia d. and this package with no problem, and synaptic doesn't show any broken packages. I don't know what it might be.
thanks a lot anyway

---

