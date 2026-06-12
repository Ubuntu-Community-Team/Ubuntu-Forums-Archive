---
title: "Looking for a linux WiFi card on newegg"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by Cyber Akuma on 2007-03-01
I have had years of expirence with Windows but know very little about Linux, so since I had some extra systems lying around there were not in use I decided to install Ubuntu on one of them to try it out. My linux system is very far away from my router and I do not have any space to put it in the same room, so I decided to try to connect it to my network by WiFi.

Problem is, I am having trouble trying to find a decent WiFi card for it. I am looking for an internal PCI WiFi card that will support 128bit WPA in Ubuntu, the best I could find was one that only supported up to 64Bit WPA.

Does anybody know of one? Preferably one that is sold at newegg if possible.

I tried using a Knoppix LiveDVD on another system before but since my home network is not configured for DCHP (long story) it would crash on boot when it detected a WiFi card but failed to obtain an IP by DCHP with it, would this be a problem with Ubuntu?

---

### Post by benfindlay on 2007-03-01
Never had much luck myself with wifi on linux, but as far as I am aware any card that has the PRISM II chipset is generally well supported. So if you can find a card that has the stuff you want, I'd suggest checking the tech specs on the manufacturer's website to see what chipset it uses.

I also know that there is some support for the RTL-818x series of cards as that is what I have in my laptop; however, I have never managed to get WPA to work with this card, just WEP.

It maywell be worth your while installing the network-manager package in synaptic as this can provide some valuable information on your network cards too!

Hope this helps!

---

### Post by slayerboy on 2007-03-01
I did some searching on Google for this and came up with a page that's close to 2 years old but still pretty relevant as Wireless cards really haven't changed much in 2 years.

[http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/](http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/)

Prism chips are what you want to look for, but a lot of chipset manufacturers can change their stuff too.  I know Linksys includes some kind of drivers for some of their wired stuff for Linux, not sure about wireless.  Check out Buffalo Technologies too.

Definitely going to have a hard time finding a product that is going to specifically say it lists Linux on it, otherwise you'd have a ton of people saying that brand x specifically supports linux.

---

### Post by Quillz on 2007-03-01
If you can find a D-Link DWL-1320 on Newegg, buy it. It works perfectly with Ubuntu.

---

### Post by Cyber Akuma on 2007-03-01
Argh, sorry for the confusion everyone, I meant WEP, not WPA.

---

### Post by benfindlay on 2007-03-01
Well, if you're just wanting WEP, then I definitely recommend any cards that support the PRISM II chipset. Many linksys cards do I believe, but they're not brilliant cards. Having looked online, there are a fair few people who like the orinoco cards (made by Proxim I believe). You can get drivers for them off sourceforge too I think. I believe that most PRISM II chips work pretty much straight away with live cds like knoppix, so there should be very little config needed to get them to work with your system!

Personally I think its much easier just to go buy a long ethernet cable and be done with it! ;)

---

### Post by Talon2 on 2007-03-01
> **Cyber Akuma said:**
>  I am looking for an internal PCI WiFi card that will support 128bit WPA in Ubuntu, the best I could find was one that only supported up to 64Bit WPA.

Does anybody know of one? Preferably one that is sold at newegg if possible.



This is what I use: (In client mode)

[http://www.newegg.com/Product/Product.asp?Item=N82E16833127138](http://www.newegg.com/Product/Product.asp?Item=N82E16833127138)

There are multiple advantages to this solution over a PCI card:

- No wifi driver needed.  If your NIC is supported then this box is supported.

- You can place the box/antenna easily in a higher/better location for reception.

- Configuration/monitoring is via Firefox.  No wifi utilities needed.

- Very easy to move to a different computer.

For me, this is solution "Just Works (tm)".

---

### Post by Cyber Akuma on 2007-03-01
> **Talon2 said:**
> This is what I use: (In client mode)

[http://www.newegg.com/Product/Product.asp?Item=N82E16833127138](http://www.newegg.com/Product/Product.asp?Item=N82E16833127138)

There are multiple advantages to this solution over a PCI card:

- No wifi driver needed.  If your NIC is supported then this box is supported.

- You can place the box/antenna easily in a higher/better location for reception.

- Configuration/monitoring is via Firefox.  No wifi utilities needed.

- Very easy to move to a different computer.

For me, this is solution "Just Works (tm)".

I was looking for something like this before but its just too expensive, getting a WiFi card for my systems would be cheaper, as well as probably easier.

I was originally looking at this:
[http://www.newegg.com/Product/Product.asp?Item=N82E16833129031](http://www.newegg.com/Product/Product.asp?Item=N82E16833129031)

But it seems that WEP or WPA above 64bit isnt supported in ubuntu.

---

### Post by reylafo on 2007-03-01
Help is on the way!
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by slayerboy on 2007-03-01
> **Cyber Akuma said:**
> I was looking for something like this before but its just too expensive, getting a WiFi card for my systems would be cheaper, as well as probably easier.

I was originally looking at this:
[http://www.newegg.com/Product/Product.asp?Item=N82E16833129031](http://www.newegg.com/Product/Product.asp?Item=N82E16833129031)

But it seems that WEP or WPA above 64bit isnt supported in ubuntu.
In this instance, I would maybe stick with a little bit more well known brand or go with the access point.  In all honesty, yes the access point is more expensive, but compared to a good wifi card, you're looking at maybe twice the amount of money with IMHO far less hassle because the OS is only integrating with the wired NIC, the access point you connect to is what holds all the configuration and utilities to connect to your wireless network.  While not all that portable, it's a better option IMHO if you're looking for easy.

---

### Post by Talon2 on 2007-03-01
> **Cyber Akuma said:**
> I was looking for something like this before but its just too expensive, getting a WiFi card for my systems would be cheaper, as well as probably easier.


A PCI card may be cheaper as far as upfront cost goes but it is higher unlikely that it will be easier.

There is more to cost than the upfront $ cost.  It depends on how much your time is worth.

---

### Post by exile on 2007-03-01
I use D-link PCI card in my desktop and a D-link PCMIA in my laptop, both worked first time out of the box for me on ubuntu.

Good luck.

---

### Post by orb9220 on 2007-03-01
I have a dlink 510 rev b1 that uses the Atheros chipset. All ubuntu's work right out the gate.

---

### Post by Cyber Akuma on 2007-03-01
Would any of these work with WEP 128 though? Most cards ive been looking at seem to have trouble going past 64.

---

### Post by benfindlay on 2007-03-01
Just came across this article: [http://www.mozmarks.com/james/node/14]("http://www.mozmarks.com/james/node/14")

Looks like it might be exactly what you're looking for!

---

### Post by masteryurez on 2007-03-01
I have D-Link DWL-G520+ and Ubuntu find my card at my first bootup =)

Buy that card! Perfectly for Ubuntu!

---

### Post by Snookered on 2007-03-01
When researching for wireless I found that Netgear works well.  All you have to do copy and paste the model #
(i.e. WG511U + linux) into the manufacturer web site search bar to see if it is supported. Also I would use google and enter the model # + linux (i.e. WG511U + linux) and many times found info on how to install the drivers and set up the wireless. A lot of linux users post how-tos on thier own websites. Also check ebay, i was out bid 5 times ( at compusa stores)before getting what i wanted, but saved $50!
No product loyalty fan here, but Netgear is working for me and did not require any drivers!
Also using WG311T PCI card and WGT624 router.
[http://www.digg.com/linux_unix/HOW-TO_Configure_Netgear_WG511U_in_Ubuntu_Linux](http://www.digg.com/linux_unix/HOW-TO_Configure_Netgear_WG511U_in_Ubuntu_Linux)
[http://www.linuxquestions.org/hcl/showproduct.php/product/874](http://www.linuxquestions.org/hcl/showproduct.php/product/874)

---

### Post by Sunflower1970 on 2007-03-01
I use the D-link WDA-1320 PCI card. Doesn't look like it's on Newegg, but I did find it over on amazon.com: [http://www.amazon.com/D-Link-WDA1320-Wireless-Desktop-Adapter/dp/B000FJ5BGE/sr=8-1/qid=1172760757/ref=pd_bbs_sr_1/104-1362861-4830358?ie=UTF8&s=electronics](http://www.amazon.com/D-Link-WDA1320-Wireless-Desktop-Adapter/dp/B000FJ5BGE/sr=8-1/qid=1172760757/ref=pd_bbs_sr_1/104-1362861-4830358?ie=UTF8&s=electronics)
Also found it on compusa's site: [http://www.compusa.com/products/product_info.asp?pfp=srch1&Ntt=wda%2D1320&N=0&Dx=mode+matchall&Nty=1&D=wda%2D1320&Ntk=All&product_code=338018](http://www.compusa.com/products/product_info.asp?pfp=srch1&Ntt=wda%2D1320&N=0&Dx=mode+matchall&Nty=1&D=wda%2D1320&Ntk=All&product_code=338018)

This card just worked for me. No configuring, Ubuntu recognized it right away, I was more than thrilled with the fact I had no problems.

---

### Post by Cyber Akuma on 2007-03-01
> **Sunflower1970 said:**
> I use the D-link WDA-1320 PCI card. Doesn't look like it's on Newegg, but I did find it over on amazon.com: [http://www.amazon.com/D-Link-WDA1320-Wireless-Desktop-Adapter/dp/B000FJ5BGE/sr=8-1/qid=1172760757/ref=pd_bbs_sr_1/104-1362861-4830358?ie=UTF8&s=electronics](http://www.amazon.com/D-Link-WDA1320-Wireless-Desktop-Adapter/dp/B000FJ5BGE/sr=8-1/qid=1172760757/ref=pd_bbs_sr_1/104-1362861-4830358?ie=UTF8&s=electronics)
Also found it on compusa's site: [http://www.compusa.com/products/product_info.asp?pfp=srch1&Ntt=wda%2D1320&N=0&Dx=mode+matchall&Nty=1&D=wda%2D1320&Ntk=All&product_code=338018](http://www.compusa.com/products/product_info.asp?pfp=srch1&Ntt=wda%2D1320&N=0&Dx=mode+matchall&Nty=1&D=wda%2D1320&Ntk=All&product_code=338018)

This card just worked for me. No configuring, Ubuntu recognized it right away, I was more than thrilled with the fact I had no problems.

Yes, ive been hearing a lot about this card being pretty good for Ubuntu, but I have one question about it,which sorta extends to every card ive been recommended here.

I was looking at all these suggestions and lists, but one thing I want to know, will these cards work with WEP128? Ive seen many people and compatible hardware lists telling me which cards/usb adapters work and which ones do not, but theres almost no mention of WEP/WPA support, especially how high the support goes.

If the WDA-1320 supports WEP128 in ubuntu then it looks like it will be perfect for what I want.

---

