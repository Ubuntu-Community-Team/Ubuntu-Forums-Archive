---
title: "Xubuntu Problem"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by Taras on 2007-12-07
I have just switched from ubuntu 7 10 to xubuntu 7 10 not becouse my computer is weak but just for fun to see what its like, i have a big problme Wine inst working on in saying that it is not supported and i cant install flash player for firefox of even when i did trhough add or remove it still didnt change anything and i coulnd see videos on the web, also i had to spend some time finding codecs for my mp3. 

CAN SOME ONE HELP ME WITH THE BROWSER PLEASE i still cant install .tar flash thingy i dont know how

WHY DO I RECIVE ERROS ON XUBUNTU WHEN IT IS THE SAME LIKE UBUNTU  almost ?

---

### Post by mali2297 on 2007-12-07
Try to use Synaptic and make sure that you've got the multiverse repository enabled.
[http://ubuntuforums.org/showpost.php?p=3909497&postcount=5](http://ubuntuforums.org/showpost.php?p=3909497&postcount=5)

Tell us what the error messages say *exactly*.

---

### Post by Atow on 2007-12-07
Are you running 64-bit xubuntu?

---

### Post by Taras on 2007-12-07
Oh thank u guys it was u had to in synaptic manager i had to eneble the repositary which had all the codecs and support for browser too thanks a lot

---

### Post by daradib on 2007-12-08
Regarding the flash player:

This is a very recent bug, caused by Adobe's update of Flash 9.0 update 3 (9.0.115.0) codename "Moviestar" on December 4th.

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

