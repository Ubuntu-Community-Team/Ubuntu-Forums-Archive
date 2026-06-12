---
title: "Dapper to Edgy upgrade issues"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by lantu on 2007-04-28
Hi,

I've been trying to upgrade from Dapper to Edgy. I did an update and upgrade as follows:

************************************************************
sudo aptitude update && sudo aptitude upgrade
gksudo "update-manager -c -d"
***********************************************************

The following showed up:

***********************************************************
/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
***********************************************************

However, the update manager provided the option to upgrade, and I duly clicked on it. The upgrade went on for a couple of minutes and the following error showed up everytime (three tries):

*************************************************************
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)
*************************************************************

Any inputs would be appreciated.

---

### Post by [S|G] on 2007-04-28
Take a look at Tauru's response at this thread: [http://ubuntuforums.org/showthread.php?t=426674](http://ubuntuforums.org/showthread.php?t=426674)
It might be related to that.

---

### Post by lantu on 2007-04-28
Thanks, but there is no repository with "us" in my sources list.

---

### Post by [S|G] on 2007-04-28
I suppose you could try to add a specific country prefix to it, such as br.archive, ar.archive, etc.

---

### Post by lantu on 2007-04-28
It already has a "ca" before it.

---

### Post by rangi500 on 2007-04-29
I'm having the same problem :-(
Any help much appreciated,
Rangi

---

### Post by mendingo84 on 2007-04-29
guys, if you want a smooth install, get the edgy CD, burn it, boot it and install. i know you'll have to manually reinstall all your apps but at least it will work smoothly. that's the way i do it at least...your option :popcorn:

---

### Post by lantu on 2007-04-29
SOLVED!

Thanks to [S|G], I looked carefully through the sources.list again and found a couple of lines that started like this

*********************************
http. archives..........
*********************************

I added a prefix for the country (ca, in my case) i.e., 

**********************
http.ca.archives......
**********************
and the upgrade went on like a charm. Typing this from the newly upgraded system.

Thanks for all your inputs.

---

