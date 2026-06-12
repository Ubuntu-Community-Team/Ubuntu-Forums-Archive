---
title: "Can't install k3b - libc6 dependency issue"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by ricardisimo on 2007-06-17
At first I thought I was facing a never-ending string of unmet dependencies, but eventually the all led to libc6, which oddly enough is already installed - just not the version k3b wants. In case anyone wants more detail:
First, trying to install k3b - ```
Could not mark all packages for installation or upgrade
The following packages have unresolvable dependencies. Make sure that all required repositories are added and enabled in the preferences.
k3b:
 Depends: transcode but it is not going to be installed
```
Then attempting to install transcode - ```
transcode:
 Depends: libavcodeccvs51 but it is not going to be installed
 Depends: libpostproccvs51 but it is not going to be installed
```
Ugggh!... OK, let's try one of these - ```
libavcodeccvs51:
 Depends: libamrnb2 but it is not going to be installed
 Depends: libamrwb2 but it is not going to be installed
 Depends: libavutilcvs49 but it is not going to be installed
  Depends: libc6 (>=2.5-5) but 2.5-0ubuntu14 is to be installed
 Depends: libfaad0 (>=2.5) but it is not installable
 Depends: libx264-54 but it is not going to be installed
```
No, say it ain't so... - ```
libamrnb2:
  Depends: libc6 (>=2.5-5) but 2.5-0ubuntu14 is to be installed

libamrwb2:
  Depends: libc6 (>=2.5-5) but 2.5-0ubuntu14 is to be installed

libavutilcvs49:
  Depends: libc6 (>=2.5-5) but 2.5-0ubuntu14 is to be installed

libx264-54:
  Depends: libc6 (>=2.5-5) but 2.5-0ubuntu14 is to be installed
```
Hmmm... they all lead back to libc6, which, like I said, is already installed, just that what I have is either too new or too old.

Any thoughts? Thanks in advance.

---

### Post by HotShotDJ on 2007-06-17
Are you using K3b from the repositories or have you downloaded something separately?

---

### Post by ricardisimo on 2007-06-18
From the repos. I had tried about 2-3 weeks ago to install the newest version of k3b, because of some bug with the repo version involving "normalize-audio". It didn't install properly, and I had to undo the damage via aptitude. Maybe it never really repaired properly, because k3b eventually showed up in the Update Manager window, but it couldn't be selected because of - you guessed it - dependency issues.

Still, the version I was working with up until a few days ago was indeed the repo version.

---

### Post by HotShotDJ on 2007-06-18
Ok... that makes sense then.  I tried the same thing, except I got the "broken" message before I actually installed the newer version of K3b.  Make sure you have deleted the package that you downloaded.  Next, open a terminal and type:```
sudo apt-get autoclean && sudo apt-get update
```Now, open Synaptic (Ubuntu) or Adept Manager (Kubuntu) and see if the proper version appears.  If this doesn't work, I really don't know what else to try.

---

### Post by ricardisimo on 2007-06-18
That seems to have done the trick. It's downloading right now. Thanks a mil.

---

### Post by ricardisimo on 2007-06-18
Oops! Spoke too soon:
```
An error occured

The following details are provided:
E: /var/cache/apt/archives/libmjpegtools0c2a_1%3a1.8.0-0.2ubuntu3_i386.deb: trying to overwrite `/usr/lib/libmjpegutils-1.8.so.0.0.0', which is also in package libmjpegtools0
```

---

### Post by ricardisimo on 2007-06-18
It just gets worse and worse. I allowed myself to get snookered into autoremoving a bunch of apps ```
The following packages were automatically installed and are no longer required:
  libgtkhtml3.8-19 scim-modules-table libneon26 linux-headers-generic debhelper python-at-spi libnl1-pre6 desktop-effects
  libresid-builder0c2a compiz-gtk libdecoration0 scim-tables-additional libipod-cil m4 ncurses-term python-virtkey restricted-manager
  libipodui-cil compiz-plugins libxcb1 gnome-orca dhcdbd boo libaudacious4 avahi-autoipd pax openprinting-ppds openoffice.org-help-es
  openoffice.org-help-fr libxcb-xlib0 libsidplay2 onboard html2text compiz compiz-core python-orca-brlapi compiz-gnome
Use 'apt-get autoremove' to remove them.
``` that were probably not doing any harm at all, and still I'm getting Update Manager and Synaptic error messages:
```
Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.
```
Once again transcode is broken, and when I try fixing it in Synaptic or apt-get install -f:
```
E: /var/cache/apt/archives/libmjpegtools0c2a_1%3a1.8.0-0.2ubuntu3_i386.deb: trying to overwrite `/usr/lib/libmjpegutils-1.8.so.0.0.0', which is also in package libmjpegtools0
```
This is all very frustrating. On the plus side, k3b is installed. I'm not sure if it is going to work properly with the problems listed above. We'll see. Any further help is appreciated.

---

### Post by ricardisimo on 2007-06-18
What is this error I'm getting now?
```
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libmjpegtools0c2a_1%3a1.8.0-0.2ubuntu3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
Thanks again.

---

### Post by ricardisimo on 2007-06-19
Resolved:
```
sudo dpkg -P --force-depends libmjpegtools0 && sudo apt-get install -f
```
Many thanks to Daniel Chen at Launchpad for this solution.

---

