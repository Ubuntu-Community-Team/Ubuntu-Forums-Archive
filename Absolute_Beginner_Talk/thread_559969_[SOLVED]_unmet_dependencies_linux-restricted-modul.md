---
title: "[SOLVED] unmet dependencies linux-restricted-modules"
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by Meph1st0 on 2007-09-25
I'm trying to follow this how to: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

When I try to install the linux-restricted-modules I'm getting the following: 

Unpacking linux-restricted-modules-2.6.20-16-generic (from .../linux-restricted-modules-2.6.20-16-generic_2.6.20.5-16.29_i386.deb)...
dpkg-deb: subprocess paste killed by signal (Broken pipe)
dpkg: error processing /var/cache/apt/archives/linux-restricted-modules-2.6.20-16-generic_2.6.20.5-16.29_i386.deb (--unpack): short read in buffer_copy (backend dpkg-deb during './lib/linux-restricted-modules/2.6.20-16-generic/nvidia_legacy/nv-kernel.o')
Errors were encountered while processing: /var/cache/apt/archives/linux-restricted-modules-2.6.20-16-generic_2.6.20.5-16.29_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

FYI: I typed all that up myself so there might be typos.

I've read up on the problem and I've seen many other people have come across similar problem with one program or another.  

I've tried: sudo apt-get -f install
but that doesn't work.

I've done: sudo apt-get dist-upgrade
but that doesn't work

I've tried: dpkg -force-remove package
but that didn't work either.

I started this project following the how to on setting up a MythTV Backend: [https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend](https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend)

it mostly went okay but I think I need to install the ATI drivers because I was getting choppy video so that led me to follow the What's next section: [https://help.ubuntu.com/community/MythTV/Install/WhatNext/Feisty?action=show&redirect=MythTV%2FInstall%2FWhatNext%2FFesity](https://help.ubuntu.com/community/MythTV/Install/WhatNext/Feisty?action=show&redirect=MythTV%2FInstall%2FWhatNext%2FFesity)

In the what's next section the ATI driver install didn't work so then I went on to the Binary Driver page: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Please help.

---

### Post by nonewmsgs on 2007-09-25
try envy.  it says nvidia, but it works for ati too.

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by Meph1st0 on 2007-09-25
I downloaded the envy_0.9.7-0ubuntu11_all.deb file from the website and then at the command prompt I typed dpkg -i envy_0.9.7-0ubuntu11_all.deb and got the following.

(Reading database ... 30669 files and directories currently installed.)
Preparing to replace envy 0.9.7-0ubuntu11 (using envy_0.9.7-0ubuntu11_all.deb) ...
Unpacking replacement envy ...
dpkg: dependency problems prevent configuration of envy:
 envy depends on xserver-xorg-dev; however:
  Package xserver-xorg-dev is not installed.
 envy depends on pkg-config; however:
  Package pkg-config is not installed.
 envy depends on module-assistant; however:
  Package module-assistant is not installed.
 envy depends on fakeroot; however:
  Package fakeroot is not installed.
 envy depends on dh-make; however:
  Package dh-make is not installed.
 envy depends on debhelper; however:
  Package debhelper is not installed.
 envy depends on dpatch; however:
  Package dpatch is not installed.
dpkg: error processing envy (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 envy


Keep in mind that this was installed as a command line box.  I do not have ubuntu-desktop installed.  It looked like envy might have been a gui config program.  I couldn't get it installed anyway.

Any other ideas?

---

