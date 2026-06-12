---
title: "Looking for help with USB Wireless connection"
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by Apocalypse King on 2006-08-20
Hello all! I'm a bit of a Linux newbie (although I've dabbled in it in the past), but I've decided to choose Ubuntu (Dapper Drake) as the distribution which I will use. 

Unfortunately, every time I try installing Linux, (I've tried Fedora and Slackware in the past), I come across the same problem; I cannot get my BT Voyager Wireless USB adapter to work properly, and as a result, cannot connect to the internet. 

Now, I've looked around the internet and I found [this very handy troubleshooting guide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide"). I printed out a copy of this and went back into my Ubuntu installation, and went through the steps, and from what I gathered:

* The device is recognised by Linux (however lsusb describes it as a 'Generic USB Device', is this bad? It also needs to be unplugged and re-plugged in before the wireless device appears on the list in the network settings. Is there a way around that? It plugs in at the back and it's fiddly to get to. I don't want to have to plug it back in every time I start the computer up.)

* The device is assigned a driver by Linux, which I *think* is the right driver, but I'm not completely sure. I'll find the name of it later.

* The device is not connecting to the router. When I use the command 'sudo iwlist wlan0 scan' it thinks for a moment and then says that the device is unavailable.

Now, I am not sure what to do. I have tried changing the settings on my router, changing the security settings, even temporarily switching WEP encryption off, but I can't seem to get this device to work in Linux.

Ultimately, this is the same problem that stopped me from using Linux the last few times I've tried it, but this time I am determined! 

Specifically, the device in question is a BT Voyager 1010 USB adapter, which connects to a BT Voyager 2000 router (I am assuming that the type of router isn't really important, and that the wireless USB adapter is the important part to configure in Linux).

Any help here would be wonderful. Apologies if this seems newbie-ish, I don't know too much about Linux yet, and it's hard to really learn much when I have to log out of Linux and back into Windows to look up information on the internet! Also, sorry if this post is rather long-winded. Hopefully someone out there will make sense of it. Thanks in advance for any help, and if any more information is needed, I will try my best to find it.

---

