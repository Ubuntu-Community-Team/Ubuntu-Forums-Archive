---
title: "Super newbie questions about wireless"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by Lucifiel on 2007-08-21
If for example: I want to set up a wireless network shared within 3 computers(1 desktop, 2 laptops), what I'd need to get is this, right? 

Btw, only 1 laptop is wireless ready. I'm going to get a wireless card for my current pc and a dongle or something for the other laptop. 

Btw, I live in Singapore so I think many of the products available in Europe and America would either not be available here or would be at 2.5x to 3x the pricing.  

- a wireless modem(supplied by the ISP)
I'm looking at 2 different ISPs. One is Qmax which likely offers the Ripwave modem. I don't know if it is ethernet or usb or both. 

The other is Singnet. I'm not too sure about their modem but I hope it's compatible with Linux.  

- a router with switch that supports BTing, multiple connections, etc., and which will remain stable when sharing between 3 computers

- wireless card(likely with Atheros chipset)
- a dongle/adaptor for non-wireless ready laptop

Is there anything that I missed? :O

---

### Post by WebSiteGuru on 2007-08-21
> **Lucifiel said:**
> Btw, only 1 laptop is wireless ready. I'm going to get a wireless card for my current pc and a dongle or something for the other laptop.

You only need 1 PCI wireless card (your brand of choice), and PCMIA wireless card for your other laptop (again, your brand of choice).
 
> **Lucifiel said:**
> 
Btw, I live in Singapore so I think many of the products available in Europe and America would either not be available here or would be at 2.5x to 3x the pricing. 

Understandable.

 
> **Lucifiel said:**
> 
- a wireless modem(supplied by the ISP)
I'm looking at 2 different ISPs. One is Qmax which likely offers the Ripwave modem. I don't know if it is ethernet or usb or both. 

The other is Singnet. I'm not too sure about their modem but I hope it's compatible with Linux. 

- a router with switch that supports BTing, multiple connections, etc., and which will remain stable when sharing between 3 computers


Recommending getting the one with the ethernet connector, it will work best in your favor. Also, request the modem that will work as Wireless Router, and modem (if they can provide one) so yopu dont have to go out and buy the router.

> **Lucifiel said:**
> 
Is there anything that I missed? :O

That should be it. Now all you have to do is configure it. :D

---

### Post by Lucifiel on 2007-08-21
> **WebSiteGuru said:**
> You only need 1 PCI wireless card (your brand of choice), and PCMIA wireless card for your other laptop (again, your brand of choice).
 

Hmmm... really? I did find out that some models are incompatible with linux, so I guess that limits my choices by quite a bit.

> Recommending getting the one with the ethernet connector, it will work best in your favor. Also, request the modem that will work as Wireless Router, and modem (if they can provide one) so yopu dont have to go out and buy the router.
I don't think they provide a lot of choices. Cost is a huge issue for most businesses here. 

> 
That should be it. Now all you have to do is configure it. :D
Thank you for your advice. There's another hitch, though. I just found out that Qmax uses 802.16(Wimax) while the wireless ready laptop supports 802.11b/g. 

This would be a compability issue, right?

---

### Post by raijinsetsu on 2007-08-21
I don't think we have 802.16 here(U.S.) yet... But I'm pretty sure 802.11 and 802.16 are not compatible at all. However, it would be very odd to supply a house with 802.16... it's meant for larger areas.

---

### Post by Lucifiel on 2007-08-21
> **raijinsetsu said:**
> I don't think we have 802.16 here(U.S.) yet... But I'm pretty sure 802.11 and 802.16 are not compatible at all. However, it would be very odd to supply a house with 802.16... it's meant for larger areas.

*shrugs* Well, it's meant to be usable as you move around an area. Oh well.

---

### Post by WebSiteGuru on 2007-08-21
> **Lucifiel said:**
> *shrugs* Well, it's meant to be usable as you move around an area. Oh well.

You might want to check to see if it is backward compatible to 802.11b/g. Some are made that way. So you can connect using any media type. Never hurt to look into it.

---

### Post by raijinsetsu on 2007-08-21
Yeah... But 802.16 is meant for up to a 31 miles(~50km), and can be as slow as 15mbps for mobile systems ([Source]("http://www.javvin.com/protocolWiMAX.html")). Pretty sure that a router that supported both would require separate antennae(anyone know for sure?).

---

### Post by WebSiteGuru on 2007-08-21
> **raijinsetsu said:**
> Yeah... But 802.16 is meant for up to a 31 miles(~50km), and can be as slow as 15mbps for mobile systems ([Source]("http://www.javvin.com/protocolWiMAX.html")). Pretty sure that a router that supported both would require separate antennae(anyone know for sure?).

From what I understand looking at the source, it tell me that there is a range of 100 meters, and speed at 55mbps. That is standard in 802.11g. That 15mbps is for the 802.16 mobile (I think).

---

### Post by Lucifiel on 2007-08-21
Bah, in the end, we're going back to the 3mbps connection again(1mbps split among 3 comps = definite "no no"). So, it's back to 802.11b/g standards.

Btw, what is a good wireless card which will work with Linux? 

If the ISP still offers a Speedtouch ST536v6, then I'm likely getting either a Buffalo G54S or a DLink 524UP.

---

### Post by Lucifiel on 2007-08-22
I'm intending to purchase a WHR-G54S when I get the new connection. However, I'd like to know if it's able to handle connections from 3 computers and also, I can pair it up with an ethernet modem, right?  

I've not yet decided whether to go wireless for all computers or use a wired connection for the laptop with no PCMIA/Bus card. Or does the "wired option" only work under Windows XP with "shared internet connection"? 'Cos as far as I know, I thought a router can't do BOTH wired and wireless modes at once.

---

### Post by fenway on 2007-08-22
I'm intending to purchase a WHR-G54S when I get the new connection. However, I'd like to know if it's able to handle connections from 3 computers and also, I can pair it up with an ethernet modem, right?  

[COLOR="RoyalBlue"]I'm not quite sure what is the spec of WHR-G54S and you might want to check on that, but usually it will have a few ethernet ports, 1 to connect to ADSL/cable model and few more to wired clients. It can technically supports up to 254 clients and hence 3 pcs will not be an issue. However there are many other TW/China brand of wireless router available. You might want to check it out on this coming IT show starting 28 Aug @ Suntec[/COLOR] 

I've not yet decided whether to go wireless for all computers or use a wired connection for the laptop with no PCMIA/Bus card. Or does the "wired option" only work under Windows XP with "shared internet connection"? 'Cos as far as I know, I thought a router can't do BOTH wired and wireless modes at once

[COLOR="RoyalBlue"] yes, as long it is a wireless router, it can support both wired and wireless connection. I dont recommend using Win XP shared internet connection.. I believe the provided ADSL model by SingNet has 2 ports, ethernet and USB. so you can have 2 PCs connected for the time being.. and if u decided to have your 3rd PC/notebook connected as well, then u can consider buying the wireless router..[/COLOR]

---

