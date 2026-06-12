---
title: "Configuring WiFi (Prism2) on Thinkpad R31"
date: 2006-03-24
forum: Absolute Beginner Talk
---

### Post by lkvee on 2006-03-24
Breezy detected the miniPCI Intersil combo-card (modem/WiFi) and setup interface eth0 but I'm not sure what else I need to do after configuring and activating WiFi.  I'm using DHCP instead of a static IP address.

I did notice another interface (eth3) when I powered up the Thinkpad in another WiFi location.   I still wasn't able to access the Internet via WiFi.

I went into Synaptic and pretty much installed any package featuring the word "Prism2".   I know I installed at least one package featuring drivers for that chipset.

I don't have the Thinkpad in front of me, but I can provide more output later, especially the results of the "lspci -vv" command.

What else do I need to do to get this WiFi setup working?   After seeing at least one package mentioning drivers for my chipset, I wasn't sure if I still needed to run ndiswrapper.

I'm also looking for the packages and applications that will seek networks, evaluate their signal strength, and connect to them.  So far, I see Prismstumbler, but it's not working, presumably because the WiFi isn't working.   I'll be reading more about "wireless-tools".

Thanks for reading.

---

### Post by mdmarmer on 2006-03-24
I think this article applies -- it indicates that you do need to use ndiswrapper

[http://bluxte.net/blog/2005-10/16-47-25.html](http://bluxte.net/blog/2005-10/16-47-25.html)

[https://wiki.ubuntu.com/SetupNdiswrapperHowto](https://wiki.ubuntu.com/SetupNdiswrapperHowto)

;-)

Mike

---

### Post by lkvee on 2006-03-26
My WiFi's working now.   Thanks for those two links.   My biggest challenge was identifying the right drivers since I couldn't find an exact entry for my particular card (the mini-PCI combo card from Harris Semiconductor).   The PCI IDs for this card match those of the Netgear MA311 card.   Works like a charm.

I'm just figuring out the rest now.   When I tell KWiFiManager to Scan for Networks, I get a dialog box telling me "The scan is complete, but no networks have been found".   WiFi Radar comes up empty but also tells me I'm "Connected to none ip(and gives an IP address right here)".

Any other applications I can install and try out.   I'm going to research AirSnort.  Other thoughts are welcome!

Thanks for the help!

---

