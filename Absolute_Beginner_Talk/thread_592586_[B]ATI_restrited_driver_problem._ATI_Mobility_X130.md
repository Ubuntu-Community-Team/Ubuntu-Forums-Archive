---
title: "[B]ATI restrited driver problem. ATI Mobility X1300[/B]"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by JakeTheMan on 2007-10-26
When I'm trying to enable the restricted ATI driver it says that I must fix broken packages. This probably means that I have to go into the Synaptic Package Manager and first install xorg-driver-fglrx. But when I try to install the xorg it says that it depends on **libstdc++5**.

When I'm reading the howto-manuals here on the forum it seems that one should be able to install the libstdc++5 via the commando: sudo apt-get install module-assistant build-essential fakeroot dh-make debhelper debconf libstdc++5 linux-headers-generic

This doesn't work for me and it seems like I'm the only one not getting this to work. It says that it can't find the module-assistant package.

Any ideas??

This is driving me nuts. I really want this to work. Strange thing is that when i tried the live-cd i was able to install the restricted driver just by enabling it. It requiered a restart and offcourse it was gone when I had restarted. I'm thinking if i could try to reinstall Gutsy again. First run the live cd and enable the restricted driver and before restarting, try to install Gutsy. Will restricted driver installation have any effect on the Gutsy installation?

---

