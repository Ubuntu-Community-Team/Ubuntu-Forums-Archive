---
title: "Driver troubles."
date: 2006-02-28
forum: Absolute Beginner Talk
---

### Post by Karisson on 2006-02-28
I'm new (*brand* new) to Ubuntu. I just installed it a few days ago on an old PC I had lying around. I completely love the interface and the bundled programs. My only problem is with drivers. I have a wireless network, and I'm trying to get my Linksys WUSB54GS Wireless-G USB Network Adapter to run. It's not a problem with the USB drivers, my USB mouse works, and the network adapter definitely works in my other computers. I've already asked in #ubuntu, and they referred me to here. Could someone point me to a driver that would get my network adapter working properly? Thanks for any help you can give me.

---

### Post by untwisted on 2006-02-28
Glad you're liking Ubuntu thus far, and I hope things work out for you.

I'm always playing with my wireless stuff, and for the longest time had hell getting it working.  My best suggestion is to check out ndiswrapper ([http://ndiswrapper.sourceforge.net)](http://ndiswrapper.sourceforge.net)).  What ndiswrapper does is uses the native Windows drivers for your card.  Ndiswrapper comes with Ubuntu (at least it has since 5.04 I *believe*) and may work for your card.  I'm trying to find the list of known working cards, but for now it eludes me.

After a bit of googling (not much mind you), it looks like the driver from [www.prism54.org](www.prism54.org) may work as well, though I'd have to recommend going for Ndiswrapper first.

Best of luck!

---

