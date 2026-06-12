---
title: "Flash not working in Konqueror"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by N1ghtm4r3 on 2007-12-08
for some reason i cannot install flash properly into konqueror. me and ardchoille looked over the problem. it seems it was caused by a previous installation of ubuntu studios. is there a way to fix it or a 'recovery' button? or do i simply have to reinstall (could be done actualy , i dont have much data to save so far)

Thanks in advance

---

### Post by kajillin on 2007-12-08
im not sure if this will work but there is an outdated package uninstaller for kubuntu, try to use that and remove the old packages for the studio. but dont remove all on the list because some arnt actually unused :P

---

### Post by daradib on 2007-12-08
BTW

There is a very recent bug, caused by Adobe's update of Flash 9.0 update 3 (9.0.115.0) codename "Moviestar" on December 4th, that causes a failure to install Flash via the flashplugin-nonfree (what Firefox does) package,

[http://www.adobe.com/aboutadobe/pressroom/pressreleases/200712/120407adobemoviestar.html](http://www.adobe.com/aboutadobe/pressroom/pressreleases/200712/120407adobemoviestar.html)

This caused Ubuntu to not install the flash plugin, detecting a change in the flash plugin installer file (via MD5 checksums). See [bug 173890]("http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/173890"). This bug has been fixed in the next release of Ubuntu (Hardy 8.04) and it should soon come as an update to Ubuntu 7.10.

If you want an immediate fix, do the following.

Using Synaptic Package Manager, remove the package flashplugin-nonfree. For more information on how to do this, see the Ubuntu documentation here: [https://help.ubuntu.com/7.10/add-applications/C/advanced.html#synaptic](https://help.ubuntu.com/7.10/add-applications/C/advanced.html#synaptic)

Alternatively, you can run this command in the Terminal (Applications -> Accessories -> Terminal): sudo apt-get remove flashplugin-nonfree

Then just download this package (32-bit only) and install it (it is identical to the current package in the next release of Ubuntu, Hardy 8.04): [http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb](http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb)

If you have 64-bit Ubuntu, you currently need to build a binary package from this source package: [http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/9.0.115.0ubuntu2](http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/9.0.115.0ubuntu2)

---

### Post by buzzz on 2007-12-09
I've done this and it works fine in Firefox, but get a segfault in Konqueror.

Backtrace as attachment

---

### Post by daradib on 2007-12-09
> **buzzz said:**
> I've done this and it works fine in Firefox, but get a segfault in Konqueror.

Backtrace as attachment

I'm sorry, but I don't have a clue what the problem is. Perhaps the new version of flash has problems with Konqueror (or vice versa).

---

### Post by daradib on 2007-12-10
For more information on this bug, see [http://ubuntuforums.org/showthread.php?p=3929669](http://ubuntuforums.org/showthread.php?p=3929669)

Take special notice of the section Apparent Problems with this Fix

---

