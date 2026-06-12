---
title: "The Other source distro's that you probably never heard of"
date: 2013-05-14
forum: Any Other OS
---

### Post by Rukiri on 2013-05-14
When you think about a source distrobution you probably think of Gentoo and portage, but gentoo isn't gentoo anymore as it uses stage 3 installs which if you don't know a stage3 install is basically a live iso with the needed tools to finished the install.  To break it down, you install the stage 3 tarball, configure your make.conf, locale and time settings, chroot into your system, run emerge-rsync which downloads the latest portage, install the linux kernel, grub, and linux-firmware, unmount and reboot.   That's basically a normal Gentoo install these days, I miss the stage 1 installs, I even know guys who build there gentoo system from scratch and use LFS as a base and download portage and configure it and guess what? the system is optimized from the get go, uses less cache and disk space than a normal finished gentoo install would and just runs cleaner but I'm here to talk about other and potentially better systems, and one I might consider as my main distro (after I get all my new hardware and dual boot setup with windows(gotta love gaming^^)).

:: Linux from scratch
As the name implies you build the system from scratch by hand, but if you tinkered with gentoo it's actually not that bad it just takes awhile to install and to give you an idea of how long it takes to install and compile kde it took me about 2-3 days to finish my LFS install with the kernel and grub installed and working nicely, and about a hr or so for KDE.  With Gentoo it takes me literally 35 minutes from stage 3 download to booting from grub but I also have a high speed connection and crap load of ram this also implies I sit down and don't go anywhere as I tend to move a lot.

:: Crux
Crux in many ways is similar to arch, it follows the KISS policy which stands for "Keep It Simple Stupid" and boy does it mean it, arch is great but it's falling a way from this and adding unneded complexity (systemd is a kick ace init system but bsd init scripts are still king in terms of boot time, arch was faster when it used true bsd init scripts, my system still boots in under 2 seconds, and a whopping .75 seconds from crux.   Crux has a great ports system and uses rsync similar to gentoo, but funtoo uses git and I'd kinda like to see crux's ports on git, there base system is anyway so why not ports?   Crux from the get go aims to be a quick and lightweight distrobution and you can make it what you want it, now if you like GNOME 3 you may have to do some packaging of your own as only Gnome 2 is in the official ports system but there's possibly unofficial repos for crux that have the latest and greatest gnome packages, but if you love gnome 2 crux has your back but just a quick glance it seems it's uses 2.24 not 2.36 but that was just a few packages (some I couldn't view as my works firewall thought it was entertainment? Linux isn't entertainment it's funtertainment^O^) 

:: Source Mage
Source Mage began as a distro roughly the same time as gentoo but had internal problems so it didn't catch fire but it does have a sweet package manager called sourcery and it also has what I call "The Options Menu" Which is a ncruses menu that allows you to select options for the package to build with similar to Gentoo but this works better as it REMEMBERS your choices, is it self aware? Let's hope not..  Some other great features is per package and local configuration, gentoo claims they have this but while it is true your wasting HDD space defining the Useflags and packages in package.use which means portage isn't as smart and portage needs to remember the choices you picked for your specific build.    Some downsides are that the some packages are not as up to date, btrfs progs is only 0.19 when 0.21_r1 is the current released btrfs tools, also gcc is still 4.6.3, not 4.7 like most other source distros, gentoo has 4.8 but I still recommend 4.7 for the time being unless you need C++11 features.

Source mage also have a branch off called Luna linux but the iso is dated and not well supported as with most other source mage distros, I recommend building a custom iso because it's so old.

Novice or newbie Linux users should not use a source distrobution but that doesn't mean they cant it's just not recommended, gentoo has nice documentation, source mage is bare bones(I mean the wiki is just a plain text document..), LFS is a no no for any linux newbie just stay away from it.

---

