---
title: "PCI Wireless Card"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by Brandon9507 on 2007-08-27
Hello everyone.. I'm a complete newbie to Linux and Ubuntu. I've used the Ubuntu live CD, and can't wait to make the switch to Linux. But, I haven't installed Ubuntu yet because I need some help on wireless cards. My home network must be WiFi due to space limitations. Under the live CD, Ubuntu does not recognize my Linksys PCI card. I've done research, and have found that this card is very difficult to run on Ubuntu. 

I have checked out the Wiki that lists the supported WiFi cards, but I'm still having this problem: None of the cards listed (PCI) are available to purchase at a local BestBuy, Circuit City, or CompUSA. I thought I had found my savior with the Net Gear WG311.. but before I bought the card, I noticed that is is V3, not the V2 that is listed as supported. 

So my question to the community is this.. What would be some recommendations of PCI Wireless G cards to purchase, or any advice at all for that matter.

Thank you!

---

### Post by jimrz on 2007-08-27
> **Brandon9507 said:**
> Hello everyone.. I'm a complete newbie to Linux and Ubuntu. I've used the Ubuntu live CD, and can't wait to make the switch to Linux. But, I haven't installed Ubuntu yet because I need some help on wireless cards. My home network must be WiFi due to space limitations. Under the live CD, Ubuntu does not recognize my Linksys PCI card. I've done research, and have found that this card is very difficult to run on Ubuntu. 

I have checked out the Wiki that lists the supported WiFi cards, but I'm still having this problem: None of the cards listed (PCI) are available to purchase at a local BestBuy, Circuit City, or CompUSA. I thought I had found my savior with the Net Gear WG311.. but before I bought the card, I noticed that is is V3, not the V2 that is listed as supported. 

So my question to the community is this.. What would be some recommendations of PCI Wireless G cards to purchase, or any advice at all for that matter.

Thank you!

The NetGear WG511T (the T is important) pcmia card uses the Atheros5212 chipset and madwifi driver. the one I use on my old ThinkPad 600x has worked well with all releases from breezy thru gutsy. I recently resurrected an old Inspiron 8000 for a friend , loaded feisty and got her a WG511T which , also, worked "out of the box". Had no problem locating one as several of the large chains had them, although I chose to buy from a small loacal shop. One word of caution, the firmware that ships with the card does not support WPA, so if you need it you will have to download the latest from the NetGear website and upgrade. This was very simple to get done on both cards.

---

### Post by Fonon on 2007-08-27
The DYnex Wireless card is out of the box compatible with Linux, and is made by Best Buy, so it's available there.  It's cheap, as well.

---

