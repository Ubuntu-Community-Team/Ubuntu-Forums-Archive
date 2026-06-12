---
title: "unable to install flash in swiftfox"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by rkakkar on 2008-01-09
```
$ whereis swiftfox
swiftfox: /usr/bin/swiftfox /usr/lib/swiftfox
$ sudo ./flashplayer-installer

Copyright(C) 2002-2006 Adobe Macromedia Software LLC.  All rights reserved.

Adobe Flash Player 9 for Linux

Adobe Flash Player 9 will be installed on this machine.

You are running the Adobe Flash Player installer as the "root" user.
Adobe Flash Player 9 will be installed system-wide.

Support is available at http://www.adobe.com/support/flashplayer/

To install Adobe Flash Player 9 now, press ENTER.

To cancel the installation at any time, press Control-C.



NOTE: Please exit any browsers you may have running.

Press ENTER to continue...



Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla): /usr/lib/swiftfox

WARNING: Please enter a valid installation path.

```

---

### Post by yabbadabbadont on 2008-01-10
Try installing it without using sudo.  That way it will try to install it into your personal ~/.mozilla/plugins directory.  If swiftfox doesn't call it that, then create a symbolic link called ".mozilla" that points to your swiftfox profile directory.

---

### Post by wolfen69 on 2008-01-10
here's the flash fix for firefox or swiftfox:

if you installed flash-plugin, remove before downloading and installing the following flash file.

[http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.7.10_i386.deb](http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.7.10_i386.deb)  then just click and install.

---

### Post by rkakkar on 2008-01-10
> **wolfen69 said:**
> here's the flash fix for firefox or swiftfox:

if you installed flash-plugin, remove before downloading and installing the following flash file.

[http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.7.10_i386.deb](http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.7.10_i386.deb)  then just click and install.

hey thanks! this worked.. however my youtube videos (or any flash games that i play) are VERY choppy... as if there is some lag taking place... any ideas?

---

