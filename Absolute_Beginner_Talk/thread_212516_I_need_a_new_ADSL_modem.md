---
title: "I need a new ADSL modem"
date: 2006-07-10
forum: Absolute Beginner Talk
---

### Post by Sonic Alpha on 2006-07-10
Hi all,

Following on from my [first post]("http://www.ubuntuforums.org/showthread.php?t=212070"), it seems I need to change my ADSL modem to avoid the nightmare I'm going through to try and get online using Ubuntu.

Now, I have no issue with buying a new ADSL modem, as the BT Voyager 100 is kinda limited anyway, however, I just don't know what to buy.  I want one that will work in Ubuntu (and of course Windows), do you have any suggestions?

Please keep in mind that I'm in the UK.  So sites like [Micro Direct]("http://www.microdirect.co.uk/") and [Aria]("http://www.aria.co.uk/") are where I'm looking (though any **UK** site will do).

Thank you :)

---

### Post by slimdog360 on 2006-07-10
I would assume that something like []("http://www.microdirect.co.uk/productinfo.aspx?ProductID=8633")
should work just fine. Id say your problem with your last modem would be the usb connection. Try to use the RJ45 connection next time, if you dont have one in your computer you can cheaply buy a pci lan card.
Or this one if you want the extra lan ports
[http://www.microdirect.co.uk/productinfo.aspx?ProductID=3233]("http://www.microdirect.co.uk/productinfo.aspx?ProductID=3233")

As long as you can configure it through windows you should be alright.

---

### Post by Sonic Alpha on 2006-07-10
Thank you, I will give it a try :)

And from what I've read elsewhere, yes the USB connection to my ADSL modem was the problem.  Unfortunately it doesn't come with an RJ45 connector.  But, like I said, I'll give the one you suggested a try :cool:

---

### Post by lemmy999 on 2006-07-10
Why not go the whole hog and get an adsl modem/wireless router. Ebuyer has a couple for less than £40! Connects to your computer using Cat5 cable.

---

### Post by slimdog360 on 2006-07-10
> **lemmy999 said:**
> Why not go the whole hog and get an adsl modem/wireless router. Ebuyer has a couple for less than £40! Connects to your computer using Cat5 cable.
Maybe I read it wrong but why get a wireless router and connect it via a cable?
Anyway I havent tried but Ive heard that wireless connection in Ubuntu can be a bit tricky so Id stay away from wireless if possible.

---

### Post by bigken on 2006-07-10
I agree buyt a wireless adsl modem router much easier to set up 
my linksys works great with ubuntu wired and wireless ;)

---

### Post by Sonic Alpha on 2006-07-10
I may get a wireless adsl modem/router, as I have a wireless network.  Though, I've only recently gotten more than 2 PCs, lol.

---

### Post by Kobalt on 2006-07-10
My Linksys WRT54G is working like a charm with Ubuntu 6.06, and the PCMCIA WiFi car I bought with is also working fine, and really easy to configure (without ndiswrapper or other manips...).

---

### Post by bigken on 2006-07-10
and one other good reason for using a adsl/router is they have built in firewall

---

### Post by Sonic Alpha on 2006-07-10
Yeah, I know :)

A friend has offered to give me a spare USB ADSL modem that he says works with Linux (though he uses SuSe), and I'll see how that goes. [-o< If it fails, I'll just buy a wireless router/adsl modem :D

---

### Post by dmizer on 2006-07-10
here's the deal.  usb is not meant for internet ... it's a generic data transfer port (like ps2 or serial connections).  it's too unstable for that kind of data transfer.  and even if that were not the case, it's crappy isp policy.

usb requires you to have drivers on your machine to make it work.  that means it's costing your pc space and processor just to get the internet to your machine.  that's before you even open a browser window.

if you purchase a adsl modem with ethernet connections (rather than usb type connections), all the drivers for it are contained within the modem itself.  it costs your pc nothing to make it work.  what this also means is that with an ethernet connection, unlike with usb, your modem is invisible to your operating system.  so it doesn't matter if you have msdos, or os2, or linux, or whatever you choose to plug into it ... as long as you have drivers for your network adapter (aka: nic, network interface card, ethernet card, ethernet adapter), you can get internet.

also ... you will get much higher transfer rates with an ethernet connection (something that was designed to carry internet specific traffic).

yes, they're more expensive money wise ... but usb adsl "modems" cost you more in the end.

as an asside ... it's my belief that providers are only too happy to provide (free of charge of course) usb modems for:
1) reducing overall server load by distributing hardware that has built in limitations on speed.
2) reducing server load by providing equipment that does not allow multiple machines to connect to the same service.
3) reducing overhead by being able to bulk pre-purchase, cheap connection hardware.
4) appealing to the customer by enticing them with low cost start-up fees and free/low cost modems.

remember in all things ... if it's alot cheaper than everyone else, there's probably a reason.

---

### Post by Sonic Alpha on 2006-07-10
Yeah I know, my ISP was kinda sneaky on what they gave out hardware wise.  I don't mind buying a new modem/router though, I just want to test out that other one first.

If that fails, I'm thinking of buying [this]("http://www.aria.co.uk/EmailAFriendLink.asp?IDNO=16267") (if that link fails to work, it's the "Netgear DG834G 54Mbps W/less ADSL Firewall Router" from Aria.co.uk).

---

### Post by dmizer on 2006-07-10
> **Sonic Alpha said:**
> (if that link fails to work, it's the "Netgear DG834G 54Mbps W/less ADSL Firewall Router" from Aria.co.uk).
it did fail ... sorry.
here's a link directly to netgear's site though: [http://www.netgear.com/products/details/DG834G.php](http://www.netgear.com/products/details/DG834G.php)

i tend to like to avoid items that are trying to be too much. jack of all trades, master of none type syndrome.

also, i don't see anything in the specs (with a quick glance) that says it supports pppoe.  pppoe is a pain to configure in linux.  that's something you should consider if you're going to purchase a modem/router.

either your adsl modem can handle the pppoe auth, or your router can handle the auth, or your computer can handle it.  easiest of the three would be to set up your router to handle pppoe auth.

if you're dead set on getting a multi device, make double sure it's going to be able to handle your pppoe auth.

---

### Post by Sonic Alpha on 2006-07-10
So, what do you recommend?

Update: If you check the data sheet it says: -

Routing Protocols: -
Static and Dynamic Routing with TCP/IP, VPN pass-through (IPSec, L2TP, PPTP), RIP, PPPoE, PPPoA, DNS, DHCP (client & server), RFC 1483 Static IP, Classic IP.

---

### Post by dmizer on 2006-07-10
> **Sonic Alpha said:**
> Static and Dynamic Routing with TCP/IP, VPN pass-through (IPSec, L2TP, PPTP), RIP, PPPoE, PPPoA, DNS, DHCP (client & server), RFC 1483 Static IP, Classic IP.
you should be good then.

really, it's just personal preference. there's probably little or no real reason for you to think that the multi device will perform any less than having seperate devices would.

actually, there's arguments for having multi devices.  first of all, there's one less (and critical) ethernet cable to worry about.  and without that cable, data dransfer from modem to router to pc is going to be more transparent and faster.

netgear is a good name, i would trust their eqipment.  same goes for linksys or dlink.

---

### Post by Sonic Alpha on 2006-07-10
Thank you, I'll post an update here if/when I buy one :)

---

### Post by Sonic Alpha on 2006-07-15
I bought the "Netgear DG834G 54Mbps W/less ADSL Firewall Router", and Ubuntu picked it up straight away.

My thanks to all those who helped me :)

---

