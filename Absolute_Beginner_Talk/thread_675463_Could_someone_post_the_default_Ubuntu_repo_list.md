---
title: "Could someone post the default Ubuntu repo list?"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by 449 on 2008-01-22
I would really appreciate it.

Thanks.

---

### Post by bodhi.zazen on 2008-01-22
what version of Ubuntu ?

gutsy : [http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Manual_Method_for_Adding_Repositories](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Manual_Method_for_Adding_Repositories)

---

### Post by overdrank on 2008-01-22
> **449 said:**
> I would really appreciate it.

Thanks.

Edit assuming you are using Gutsy as the profile reads.

```
deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.

deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

##Universe

deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## Multiverse

deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Backports

deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Canonical Partner Repository 

deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner
deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://packages.medibuntu.org/ gutsy free non-free
```

---

