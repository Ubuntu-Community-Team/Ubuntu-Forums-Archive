---
title: "Update manager fails"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by orangemoose on 2008-03-22
On a clean install of Gutsy 

Update manager  from the System menu fails with

"Could not download all repository indexes"

And an error box with

W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) gutsy Release: The following signatures were invalid: NODATA 1 NODATA 2
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release: The following signatures were invalid: NODATA 1 NODATA 2
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release: The following signatures were invalid: NODATA 1 NODATA 2
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports Release: The following signatures were invalid: NODATA 1 NODATA 2
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security Release: The following signatures were invalid: NODATA 1 NODATA 2


But at the command line:

sudo apt-get update runs fine.

Here is my sources.list copied from Unofficial Ubuntu website

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

##Universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe

## Multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Backports

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Canonical Partner Repository 

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security multiverse

---

### Post by zvacet on 2008-03-22
```
sudo apt-get update && sudo apt-get upgrade
```

---

