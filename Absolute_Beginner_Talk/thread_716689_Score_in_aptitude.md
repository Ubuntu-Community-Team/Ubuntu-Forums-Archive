---
title: "Score in aptitude"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by Tampert on 2008-03-06
Hi,

I would like to compile a piece of software (Scribus). For this, I need to install the xlibs-dev package. Trying to do this with aptitude yields

```
sudo aptitude install xlibs-dev
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Reading task descriptions... Done
Building tag database... Done
The following packages are BROKEN:
  x11-common
The following NEW packages will be automatically installed:
  libfontenc-dev libice-dev libsm-dev libxfont-dev libxmu-dev libxmu-headers libxmuu-dev libxp-dev libxpm-dev
  libxrandr-dev libxt-dev libxtrap-dev libxtst-dev pm-dev x-dev x11proto-fonts-dev x11proto-print-dev x11proto-randr-dev
  x11proto-record-dev x11proto-trap-dev xfree86-common xlibs-static-dev
The following NEW packages will be installed:
  libfontenc-dev libice-dev libsm-dev libxfont-dev libxmu-dev libxmu-headers libxmuu-dev libxp-dev libxpm-dev
  libxrandr-dev libxt-dev libxtrap-dev libxtst-dev pm-dev x-dev x11proto-fonts-dev x11proto-print-dev x11proto-randr-dev
  x11proto-record-dev x11proto-trap-dev xfree86-common xlibs-dev xlibs-static-dev
0 packages upgraded, 23 newly installed, 0 to remove and 0 not upgraded.
Need to get 2292kB of archives. After unpacking 6554kB will be used.
The following packages have unmet dependencies:
  x11-common: Conflicts: xfree86-common but 4.3.0.dfsg.1-14sarge5 is to be installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
pm-dev [Not Installed]
xfree86-common [Not Installed]
xlibs-dev [Not Installed]

Score is -9981

```

So now I have two questions.
1. How shouls I continue?
2. What does the "score" mean? 

I am especially curious towards question two because of my curiosity.

---

### Post by Arthur Archnix on 2008-03-06
The first thing I'd do is investigate this one:
> The following packages are BROKEN:
  x11-common

---

### Post by hyper_ch on 2008-03-06
isn't scribus in the repos?

---

### Post by Tampert on 2008-03-06
> **hyper_ch said:**
> isn't scribus in the repos?

Yes it is, but I am working with an outdated version of the repos, which is internal here and I don't have more 'rooty' access than using aptitude. That is one of the main reasons I would rather not want to break too much.

---

