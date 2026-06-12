---
title: "TriBoot on a MacBook Pro"
date: 2007-09-27
forum: Apple Intel Users
---

### Post by chipt4 on 2007-09-27
Hi, I'm rather new to linux desktop installations and have a couple of questions.

My situation:  I have a 15" MBP, 1.83ghz, 1.5gb ram, 128mb vram, 80gb HD.  I currently have OSX 10.4.10 and Windows XP SP2 dual booted via boot camp.

What I want:  I'd like to have Ubuntu Feisty on a triple boot.

My questions:  I've read a few threads/wikis about dual booting feisty with OSX, one about triple booting dapper with osx and xp, and some about gutsy hardware issues.  Pretty much, what I want to know is, how different from the dapper triple boot article would my setup be?  Have things improved any (I believe it was written almost a year and a half ago)?  Are all the hardware kinks worked out (iSight, two-finger gestures, wifi, ati drivers)?  I'm a little nervous about doing this.  The most experience I have is running feisty via parallels, and I have installed dapper on a desktop pc, but it was straightforward.

Does anyone out there have a setup similar to this?  Can you give me any pointers? Should I wait for Gutsy?

The articles I've read are:

[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)
[https://wiki.ubuntu.com/MacBookProFeisty](https://wiki.ubuntu.com/MacBookProFeisty)
[http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp_Ubuntu](http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp_Ubuntu)

I appreciate any advice you guys can give me, I'm a little intimidated, to say the least.

Also, I'm interested in compiz fusion or beryl.. Which desktop should I use, KDE or GNOME? (or does it matter? i'm partial to gnome, but kde has some nice effects) 

chip

---

### Post by cyberdork33 on 2007-09-27
The overall methods to triple boot are pretty much the same. There are also a few threads here about getting triple boot working that are probably more up to date.

iSight is still not working in gutsy, and you can get it working in feisty using the how to in this forum. [http://ubuntuforums.org/showthread.php?t=491381](http://ubuntuforums.org/showthread.php?t=491381)

 Wifi is a beast. There is a lot of information here about getting it working with madwifi and several people have problems. ndiswrapper is also an option. Both of these methods are explained in the wiki page for Macbooks that you linked to.

ATI is not really an issue (other than the feisty live cd fails to start X, and is fixed for gutsy). you are going to have to install the binary drivers if you want 3D acceleration. Getting that working is detailed in the MacbookPro wiki page you linked to under 'Fixing xorg drivers'

Two-finger gestures will not work because it is not set as the default in Ubuntu. You will always have to configure that yourself. See: [http://ubuntuforums.org/showthread.php?t=493758](http://ubuntuforums.org/showthread.php?t=493758)

Gnome vs KDE is a matter of personal choice, although more people tend to use Gnome since it is the default for Ubuntu.

---

