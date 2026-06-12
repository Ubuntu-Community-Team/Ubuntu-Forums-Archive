---
title: "Ubuntu a good multi-use server OS?"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by sdenham on 2008-02-17
Hello,

I'm looking into turning my old gaming rig into a multimedia fileserver, printserver, and maybe a router/firewall. I'm curious if Ubuntu is a good choice for it. Here's my hardware:

Antec 900 Case
Antec 900W Power Supply
Asus A8N32 SLi Deluxe (Non Wifi, but has 2xLAN ports)
AMD Athlon64 FX-60 (Dual core > all)
2x512mb OCZ DDR400 RAM
2xWestern Digital 200gb SataII
DLink WDA-2320 WiFi PCI Card (802.11b/g, 108Mbs)
XFX nVidia GeForce 8800 GTS 512MB (Probably going to down-grade, since it won't work with Ubuntu)
20" Xerox LCD Monitor (Nothing fancy)
DLink 524 WiFi "Router" (Really it's just an advanced switch)
HP 1200 Series All-In-One Printer
Plextor 750a DVD Burner

Granted, this is a bit overkill for this perpose, but it would cost me more money to buy a barebones system with enough SataII ports for what I want to do than to just buy some more HDs and a cheaper video card. I'm thinking of buying 2x500GB drives to give me a total of 1.4GB of storage (not much, but it would suit my needs). Terabyte drives are a little too pricey still (I can buy 2x500's for cheaper than 1x1TB). This mobo can handle up to 8 Sata devices, so I've got room for expansion.

Also, I'm wanting to do a wireless network, but I'm not sure if 108Mbs is fast enough if I'm going to be doing multimedia streaming (playing movies from the fileserver over WiFi). I live in an apartment, so running alot of Cat5 isn't an option. I've not kept up with WiFi technology over the last couple years, but it seems the fastest routers are only 250Mbs and even then it seems not all cards/adapters ever reach those speeds.

There are some issues with using this PC as such:
1.) Power consumption. This thing can draw some major power.
2.) Heat. It runs at 90-97 degrees during activity (idles at 84-87).
3.) Driver support for all the goodies (Both LANs, in particular)

Benefits:
1.) Has enough oomph to handle both video compression and streaming
2.) Can also use it as a Web-server if I want
3.) Can still be used to play decent games

Any suggestions on a good, cheap, compatable video card, and wether or not this is a good venture would be greatly appreciated.

Thanx,
A1C Steven Denham
Goodfellow AFB, TX

---

### Post by JoshuaRL on 2008-02-17
I'm suprised that Ubuntu doesn't recognise your graphics card.  I have an 8400GS and it works great.  I would try Envy, it should automatically install your driver for you.

Ubuntu should run pretty easy on your power consumption, but if you really want to make it easy I would suggest running it without Xserver.  It will be harder to learn and manage at first, but it will be a lot faster too.

You could always put more or bigger fans in there, but then your power consumption goes up.

As far as a server system goes, Linux is the best.  And Ubuntu is pretty great for that.  Linux is so awesome on servers that Windows is trying to play catch-up to it.

---

### Post by Kilz on 2008-02-17
Ubuntu is a great server. I have a file/web/ etc running Ubuntu. Be aware that the server install disks do not install a desktop. You can install one, there are some good desktops like icewm that are low resource. You can also consider using the 64bit version of Ubuntu since you have a good 64 bit processor.

---

