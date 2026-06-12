---
title: "WLan not scanning; wireless help needed"
date: 2006-02-17
forum: Absolute Beginner Talk
---

### Post by Benjamin Wood on 2006-02-17
Hi
I've followed several threads in trying to get my wireless card (Netgear WG511v2) working but can't even get the card alive. I'm very new to Linux.
I tried 'sudo iwlist wlan 0 scan', but it doesn't work. The terminal tells me 'Interface doesn't support scanning'.
I've ndiswrapper and the Windows driver in place, but am still at a loss. Any help?
Ben

---

### Post by metalox on 2006-02-28
Hi, I can't tell exactly what the problem is, because I have a similar problem with a Netgear WG311 (v2) wirelss PCI card.  Anyway here are some ideas:

You probably need a program called "ndiswrapper" installed. This program can use the original Windows driver for your card. To see if it is already installed just type ndiswrapper [Enter] in a terminal. If ndiswrapper is already installed you will get a few lines of usage information. If not installed you will get a "command not found" message.

Otherwise use Synaptic to install ndiswrapper and ndiswrapper-utils. From the desktop: -System -Administration -Synaptic Package Management then -Seach: "ndiswrapper"

For detailed information on setting up ndiswrapper see the ndiswrapper web site / wiki: 
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)

I also found a useful thread in this ubuntu forum, search for "netgear wireless":
[http://www.ubuntuforums.org/showthread.php?t=19978&highlight=netgear+wireless](http://www.ubuntuforums.org/showthread.php?t=19978&highlight=netgear+wireless)

Good Luck! Stick with Linux, it's worth it.;)

---

### Post by metalox on 2006-02-28
Sorry, can't read! OK, you already have ndiswrapper installed! Oh well, hope the two links can help a bit.

---

