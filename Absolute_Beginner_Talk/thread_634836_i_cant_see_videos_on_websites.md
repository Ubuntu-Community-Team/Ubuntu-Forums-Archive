---
title: "i cant see videos on websites"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by Gigantesco on 2007-12-08
i am using ubuntu and when i try to watch videos on the net its
like showing me an empy box instead of the video where it says
that i need to install an plugin to my firefox but it seems that the plugin
which the gave is for windows only.

pleasehelp me.

---

### Post by Ub1476 on 2007-12-08
Pase this command into the terminal or look for ubuntu-extras in Synaptic:

```
sudo apt-get install ubuntu-restricted-extras
```

This will install java, flash, codecs etc.

---

### Post by daradib on 2007-12-08
FYI:

There is a very recent bug, caused by Adobe's update of Flash 9.0 update 3 (9.0.115.0) codename "Moviestar" on December 4th.

[http://www.adobe.com/aboutadobe/pressroom/pressreleases/200712/120407adobemoviestar.html](http://www.adobe.com/aboutadobe/pressroom/pressreleases/200712/120407adobemoviestar.html)

This bug would cause the above instructions, which should work normally, not to work.

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

