---
title: "VMWare Bridged Networking module does not load."
date: 2006-10-06
forum: Absolute Beginner Talk
---

### Post by Giggity on 2006-10-06
[SIZE="5"]**To all good samaritans just trying to help: before suggesting a solution, please know that I [COLOR="Green"]*do*[/COLOR] in fact have the latest kernel headers installed!**[/SIZE]
With that in mind, I'll go on...

I'm restarting this thread since my last version of it was very poorly titled, so I'm sure fewer people could read it and offer a solution.

VMWare Workstation worked great until one of the latest kernel upgrades.  Since then, the module "vmnet0" for Bridged Networking fails to load.  [COLOR="Green"]Yes, I upgraded the kernel headers[/COLOR]... still didn't work.

I had given up on the whole notion of using bridged networking until I learned that there is a package in the apt database called "vmware-player-kernel-modules-2.6.15-27", which just happens to be the kernel version I'm using right now.  Trouble is, I install it, and even after running the vmware-config.pl script again, I still see bridged networking fail to load.

I'm pretty sure that the file "vmnet.ko" installed with the aforementioned package was meant to make this trouble stop happening, as it is a file mentioned during the configuration.

The file installed with the "vmware-player-kernel-modules-2.6.15-27" package is located at /lib/modules/2.6.15-27-386/misc/vmnet.ko, and the location referred to by the installation script is at /tmp/vmware-config0/vmnet-only/vmnet.ko

[LIST]
[*]Does the fact that I'm using VMWare Workstation instead of VMWare Player have anything to do with the module not loading properly?
[*]Does it have to be placed in a different directory, given that I'm using Workstation instead of Player?
[*]Can I put it somewhere in the directories that the program installs from and have it be the default version installed?
[/LIST]

The person who can solve this problem for me will retain my eternal gratitude.  But before you offer a solution, remember... [COLOR="Green"]I *do* have the latest kernel headers installed[/COLOR]!

---

### Post by Giggity on 2006-10-08
Just wondering if I'm the only one who has this problem, or if it's just taboo to discuss it here.

Things I've tried:

[LIST]
[*]Installing the vmware-player-kernel-modules-2.6.15-27 package
[*]Installing the vmware-player-kernel-source package, compiling the modules, and copying them to the /lib/modules/`uname -r`/misc/ directory
[/LIST]

Still, no matter what I do, the bridged networking module fails to load!  Does anyone have anything?  Are these modules for some reason incompatible with VMWare Workstation 5.5.2 build 29772?

The helpers here are so quick to answer my other questions about running software on Ubuntu that I'm wondering if asking about this particular problem is against the forum rules.  If it is, please let me know, and I'll stop bugging!

---

### Post by toobuntu on 2006-10-19
Haven't tried this yet, but it seems that because VMware stores the MAC address of eth0 in a file and MAC addresses change when they are used on another host, this breaks networking.

To fix: comment out the line beginning eth0 in /etc/iftab

Test:
ifup eth0
ifconfig

---

