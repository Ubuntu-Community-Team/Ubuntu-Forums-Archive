---
title: "Re-installing Network Manager"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by Udibuntu on 2007-12-03
Hi,

I've replaced Gutsy on my work T42 with Feisty 32bit.

I tried to connect to my office WLAN and got several errors, and then tried to uninstall and re-install nm-applet.

Boy, that was a stupid mistake - I can't find it in Synaptic now I can't connect to the internet...

Is there any way around this or will I have to re-install Feisty?

Thanks,

Udi

---

### Post by mikewhatever on 2007-12-03
Try
> sudo apt-get install network-manager-gnome

or search for network-manager in synaptic.

---

### Post by Udibuntu on 2007-12-03
Toda Mike.

No good, Synaptic needs an internet connection to download it.

I tried to put the LiveCD in the CDROM and to install from it but no dice.

How can I do it without internet connection??

:(

Udi

---

### Post by mikewhatever on 2007-12-04
With the live cd in cd-rom, open System>Admin>Software Sources and add the CD to the repositories. The network manager should be there. If, for some reason, it does not work, try downloading the package from here (bottom of page) [http://packages.ubuntu.com/gutsy/net/network-manager-gnome](http://packages.ubuntu.com/gutsy/net/network-manager-gnome)
There are lots of dependencies, but hopefully you have those other packages installed.

---

### Post by Udibuntu on 2007-12-04
OK, I'll try and update on results.

Thanks,

Udi

---

