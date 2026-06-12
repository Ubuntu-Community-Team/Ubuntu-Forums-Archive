---
title: "Drivers, Anyone?"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by WNxCryptic on 2007-04-12
Its been a while since I worked with Linux, and the only useful terminal commands I remember are cd, ls and lsmod, so bear with me.

Just did a clean install of Ubuntu 6.10 and everything is fine as far as getting into it and whatnot. The issue lies in the fact that apparently a wide variety of the drivers that came with this version of the distro aren't compatible with my laptop.

Before this, I installed the 7.04 beta version, which apparently included some more compatible network drivers, but other than that was essentially very sketchy which is why I reverted to 6.10.

Anyways, in 7.04 I have a little "Network Connections" icon in the top-right, next to my battery meter (although it could never connect to the wireless connection I have at home, so it was probably still a driver issue) but in 6.04 that network connection icon isn't even there. Once I get into the Network Settings under Administrator, I have 2 devices:

Wireless Connection (wmaster0) - Not configured
Wireless connection (wlan0) - Not configured

I'm presuming that, despite its name, the wlan0 is actually my PCI bus NIC..although at the moment neither is doing me any good since neither works.

This is just a starting point (since the only other thing that really works decently is my sound) but once I get the networking running on the laptop I can do all this searching / posting / driver installing from it.

oh, and also..as far as installing drivers, I'll need someone to direct me to a tutorial..I know it includes some tar -xzy and make commands, but other than that I have no idea.

---

### Post by aberry5555 on 2007-04-12
The thing with Ubuntu is that Drivers don't install in a particular way (like Windows) you can and have to use a variety of methods to configure the drivers for your system. A good start might be to list what drivers are needed on your PC. It also sounds like Ubuntu has assigned the wrong driver to your network card which is why you are getting two wireless connections. Do you by any chance know the type of network chipset you use or, if not, have the model number of your laptop?

---

### Post by WNxCryptic on 2007-04-12
Computer: Averatec 7100 Series

NIC: MSI Gigabit Ethernet (not sure on model)
-http://www.averatec.com/customercare/results.asp (Windows Driver, not sure if it helps in identifying it)

Wireless: MP54G5
Chipset: Ralink RT2561T

---

### Post by WNxCryptic on 2007-04-12
*Bump*

(Sorry, things fall off the pages incredibly fast around here..lol)

---

### Post by Sef on 2007-04-12
> I'll need someone to direct me to a tutorial..I know it includes some tar -xzy and make commands, but other than that I have no idea.


Read [How to install anything in Ubuntu]("http://monkeyblog.org/ubuntu/installing/").

---

### Post by WNxCryptic on 2007-04-12
That tutorial will at least help me with installing the drivers, now all I need is some help locating the right ones.

---

### Post by aberry5555 on 2007-04-13
well for wireless you can use the windows drivers, there is a piece of software that you can get from the repositories (synaptic) called "Ndiswrapper". Download that and also get your drivers, then follow the instructions on the ndiswrapper site on how to install it.

---

