---
title: "Netgear WPN111 USB WiFi Adapter"
date: 2010-12-20
forum: Any Other OS
---

### Post by wman2 on 2010-12-20
Hi everyone. This post is about Linux Mint.  I know it technically shouldn't be posted in this forum (sorry!), but in my experience it has a much quicker response rate than the Linux Mint forum - I've already posted there with no luck.  So here's the post:

Hi everybody.  I'm new  to Linux Mint but have been using Ubuntu for a while.  I have just  installed Linux Mint on my old computer.  The install ran fine.   However, the Netgear WPN111 USB WiFi Adapter I use on the same computer  with Windows XP isn't detected when I plug it in.  I have the Windows  drivers CD.  I found a (very long with many steps) guide to making it  work with Ubuntu, which I'm trying to use.  It says to start off with,  though, you need to install the package "build-essential".  This package  has a lot of dependencies too.  I don't have internet on this computer,  though, because the adapter won't work!  So I'm in an annoying circle.   All the packages needed are on the installation CD of Ubuntu and  presumably Linux Mint, though I installed Mint using a USB stick which I  have now lost.  I still have 2 installation discs for Ubuntu 10.10,  though, which appear to have the necessary packages on them. I have  tried "sudo apt-cdrom add", which worked.  Then, if I go into Synaptic  and tick "build-essential" and say yes to the extra dependencies, it  tries to install the dependencies from the internet repo which I can't  access, instead of the CD, which the packages are on.

Any help here?  Much appreciated.  [IMG]http://forum.linuxmint.com/images/smilies/icon_biggrin.gif[/IMG]

---

### Post by wman2 on 2010-12-22
Please?

---

### Post by HTMLCrazy on 2011-01-02
Try plugging an ethernet cable into the ethernet port on the back of the computer, and wait until it says that it is connected, then try to install the files.

---

### Post by vandamme on 2011-01-03
I'm running Mint LXDE on a 6 year old Toshiba laptop with 256M ram. The Netgear WPN111 installed pretty easy using Preferences-> Windows Wireless Drivers although it always says it couldn't find whether the hardware was present, but the program installed it anyhow. It seems to run in fits and starts, going for weeks but occasionally refusing to work whatever I do (usually runs on Windoze XP). It cost ten bucks from TigerDirect, although I'm not sure it was worth the hassle. 

Dunno what to tell ya. I just installed it with the Mint Install Wireless Driver app, found the netwpn11.inf file, and bam it was running. Didn't need any packages.

---

### Post by jeremey-key on 2011-05-28
You probably don't need this now... but for others who come across this post check out ThinkPenguin.com. They have 802.11G and 802.11N USB wifi adapters (and other types) that  just work in GNU/Linux because they are designed for GNU/Linux using an Atheros or Realtek chipset. The older 802.11G Realtek chipset does not depend on non-free firmware or drivers and the 802.11N uses an Atheros chipset which has free firmware and drivers. What that boils down to is you can be confident it will work into the future unlike the other adapters on the market which claim "Linux support" or happen to work with a particular distribution for a particular version of the card (which you can rarely get by the time you happen across the information anyway).

---

