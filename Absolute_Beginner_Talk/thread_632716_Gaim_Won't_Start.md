---
title: "Gaim Won't Start"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by esc1 on 2007-12-05
Again weird problems happening to me again.  Had a random logoff. Then had problems with slow startups. Weather panel applet had some type of crash.  Compiz fusion was having a hard time cpu wise.  Well now that appears to be okay, but I can't run Gaim.  

If I try to remove it wants to take ubuntu-desktop with it.  Look:

sudo apt-get remove gaim
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-awn python2.4-minimal python2.4 screenlets-utils libberylsettings0
  python-feedparser libxml1 libakamaru0 screenlets-extra build-essential
  screenlets-core
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  gaim nautilus-sendto ubuntu-desktop
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 5747kB disk space will be freed.
Do you want to continue [Y/n]? 

I don't get this.  

If I run from the cl all I get is:

 gaim
Segmentation fault (core dumped)

---

### Post by esc1 on 2007-12-05
I remember I turned on logging the  last time I had Gaim up.  I tried deleted my .gaim folder in home. Didn't affect anything.

---

### Post by esc1 on 2007-12-05
Well I tried to remove anyways and this is what I get:

dpkg: parse error, in file `/var/lib/dpkg/available' near line 26371 package `libgdl-1-0':
 `Depends' field, reference to `libgnomeu': version contains `)'
E: Sub-process /usr/bin/dpkg returned an error code (2)

---

