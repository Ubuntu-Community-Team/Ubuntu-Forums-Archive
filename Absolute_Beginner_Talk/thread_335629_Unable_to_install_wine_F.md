---
title: "Unable to install wine :F"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by RubberDuk on 2007-01-10
Hey folks!

In short, my problem is the following:

Err [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Packages
  404 Not Found
Fetched 933B in 0s (2233B/s)
Failed to fetch [http://wine.budgetdedicated.com/apt/dists/edgy/main/binary-amd64/Packages.gz](http://wine.budgetdedicated.com/apt/dists/edgy/main/binary-amd64/Packages.gz)  404 Not Found
Reading package lists... Done
W: GPG error: ]http://wine.budgetdedicated.com edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

Asked a friend who tells me it worked fine for him. So.. how should I proceed?
Using Edgy.

---

### Post by raul_ on 2007-01-10
what instructions have you followed in order to install it?

---

### Post by RubberDuk on 2007-01-10
Checked several, lastly this one:
[http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb)

---

### Post by raul_ on 2007-01-10
could you post your sources.list file please?

---

### Post by RubberDuk on 2007-01-10
deb [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe


deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main

---

### Post by raul_ on 2007-01-10
you can always try this:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Windows_Applications_in_Linux_.28Wine.29]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Windows_Applications_in_Linux_.28Wine.29")

I find it much easier

---

### Post by RubberDuk on 2007-01-10
The first step (adding the repositories and updating) is still the root of the problem to which neither guide really helps.

---

### Post by RubberDuk on 2007-01-10
Well, I solved it by downloading the package from here [https://netfiles.uiuc.edu/agoodri2/wine_0.9.28-1_amd64.deb](https://netfiles.uiuc.edu/agoodri2/wine_0.9.28-1_amd64.deb) and using update. Thanks anyway ;)

---

