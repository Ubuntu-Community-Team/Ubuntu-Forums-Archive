---
title: "Failing source packages?"
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by brn on 2006-10-28
I'm trying to install kubuntu-desktop on Dapper.  So far no luck.  I first executed _sudo aptitude update_, then _aptitude install kubuntu-desktop._  When it finally stopped downloading packages I saw a funny message about "postfix" which I ignored.  When I logged out/in, the "*Select Session*" option showed only "Remote login via XDMP" (whatever that is) but no KDE.

I executed _aptitude remove kubuntu-desktop_ and went through the procedure again.  Although the vast majority of packages updated gracefully, I noticed some strange reports from both apt-get and aptitude.  Some of the messages complained about packages "not in gzip format" and others "could not resolve packages.freecontrib.org".  Now that all or most of the required packages are on my disk, removal and installing appear to go very fast and end without complaint.  Here is some dialogue from a recent attempt to re-install:
```
The following packages have unmet dependencies:
  openoffice.org-common: Conflicts: openoffice.org-mimelnk but 1.1.3-9sarge3 is to be installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
gwenview [Not Installed]
kipi-plugins [Not Installed]
koffice-data [Not Installed]
koffice-libs [Not Installed]
krita [Not Installed]
kubuntu-desktop [Not Installed]
openoffice.org-mimelnk [Not Installed]

Score is 53

Accept this solution? [Y/n/q/?]
```
I accepted and a lot of package names rolled up the screen before this:
```
0 packages upgraded, 0 newly installed, 0 to remove and 194 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] 
```
0B looks like a hex digit but what it means I cannot guess.  Finishing the installation attempt produces an orderly stop.  **But no KDE.**

---

### Post by bulldog on 2006-10-28
If you look closely you can see the packages are not installed because you had something installed which not came from the Ubuntu repositories.

You can get messed up with dependency's that way.
So it can't install everything you need and can't fix the dependency's,unless you removed the 'not Ubuntu' package.

---

### Post by brn on 2006-10-28
For whatever reason, I could not install the KDE desktop with aptitude.  I finally found it in Synaptic Package Manager which reprised the whole 60 MB download (an overnighter at 56 Kb) and finished installation.  Success at last.

---

