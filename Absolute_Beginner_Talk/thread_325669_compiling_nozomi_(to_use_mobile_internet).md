---
title: "compiling nozomi (to use mobile internet)"
date: 2006-12-26
forum: Absolute Beginner Talk
---

### Post by alexmoon on 2006-12-26
Hi, I'm veryvery new to linux generally, and ubuntu in particular. I only sorted out wireless internet a few weeks ago, and then promptly left the country and started using mobile internet. So I've probably missed a basic, very obvious step somewhere - problem is that I'm not sure where.

My current problem is that I'm trying to get mobile internet working, but I suspect I've done something wrong with nozomi. 

I followed the instructions given in the howto from nickwallingford ([http://ubuntuforums.org/showthread.p...ht=huawei+E220](http://ubuntuforums.org/showthread.p...ht=huawei+E220))

As far as I can tell, changing the wvdial.conf bit went ok, but when I type "wvdial hsdpa" I get:
--> WvDial: Internet dialer version 1.56
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
--> Modem not responding.

So it seems like maybe the driver (nozomi, I hope) might be the problem? I got the package from here: [http://packages.debian.org/unstable/net/nozomi-source](http://packages.debian.org/unstable/net/nozomi-source) (from the part that said: "download nozomi-source") and then it came up with a package (nozomi-source_2.1.2_all.deb) that I clicked on and it seemed to have installed itself.

Are there other bits I was meant to install (compile?)?

I typed this: apt-cache search nozomi
and got this: nozomi-source - source for GlobeTrotter HSDPA kernel driver

I don't know if that means it's compiled or not, though.

Thank you very much for your help, I really hope I haven't done anything too stupid. I've read through "how to install anything on Ubuntu" but it hasn't helped, unfortunately.

I've also posted this in the networks section, but it seemed like it might just be a basic problem, so I asked here as well. I hope that isn't impolite.

---

