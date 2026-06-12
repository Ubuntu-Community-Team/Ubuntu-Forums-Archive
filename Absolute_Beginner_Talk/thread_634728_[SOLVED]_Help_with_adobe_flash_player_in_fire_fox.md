---
title: "[SOLVED] Help with adobe flash player in fire fox"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by famous3warriors on 2007-12-08
Absolute beginner adobe flash not working in firefox.  How do I go about fixing this problem?  I have tried to completely remove flashplugin-nonfree in synaptic manager but am I missing a step?  Pleas help and thanks for your advice.:(

---

### Post by Danikar on 2007-12-08
To install it I always went to YouTube with Firefox, click on a Flash item, it will redirect you to adobe's page.

Adobe has an installer for Ubuntu that you have to use at the console, most everything sets up right away, you might have to let it know where Firefox is located on you system.

---

### Post by famous3warriors on 2007-12-08
Ok I will try that. Thanks very much I really do appreciate this allot.

---

### Post by daradib on 2007-12-08
Flashplugin-nonfree should work, but there is a very recent bug, caused by Adobe's update of Flash 9.0 update 3 (9.0.115.0) codename "Moviestar" on December 4th.

[http://www.adobe.com/aboutadobe/pressroom/pressreleases/200712/120407adobemoviestar.html](http://www.adobe.com/aboutadobe/pressroom/pressreleases/200712/120407adobemoviestar.html)

This causes Ubuntu to not install the flash plugin, detecting a change in the flash plugin installer file (via MD5 checksums). See [bug 173890]("http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/173890"). This bug has been fixed in the next release of Ubuntu (Hardy 8.04) and it should soon come as an update to Ubuntu 7.10.

If you want an immediate fix, do the following.

Using Synaptic Package Manager, remove the package flashplugin-nonfree.

Alternatively, you can run this command in the Terminal (Applications -> Accessories -> Terminal): sudo apt-get remove flashplugin-nonfree

Then just download this package (32-bit only) and install it (it is identical to the current package in the next release of Ubuntu, Hardy 8.04): [http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb](http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb)

If you have 64-bit Ubuntu, you currently need to build a binary package from this source package: [http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/9.0.115.0ubuntu2](http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/9.0.115.0ubuntu2)

---

### Post by daradib on 2007-12-10
For more information on this bug, see [http://ubuntuforums.org/showthread.php?p=3929669](http://ubuntuforums.org/showthread.php?p=3929669)

---

