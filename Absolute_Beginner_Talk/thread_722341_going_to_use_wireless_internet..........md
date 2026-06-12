---
title: "going to use wireless internet........."
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by Nick8692 on 2008-03-12
Well, i have a belkin router, and a want a wireless internet connection on my computer with Ubuntu.  I dont know whether to buy a wireless card or a USB dongle :confused:

I would appreciate it if pople would post which card or dongle they use  that is garanteed to work with ubuntu so i can buy one.

Thanks :)

---

### Post by rbc on 2008-03-12
Have a look at this:
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by wolfen69 on 2008-03-12
from what i hear, Netgear WG111 v2 (usb dongle) works perfect out of the box in ubuntu. make sure it is the v2. i plan on getting one.

---

### Post by Nick8692 on 2008-03-12
bump

---

### Post by kamitsukai on 2008-03-12
The Dynamode WLGI700S works well on ubuntu ([http://www.ebuyer.com/product/107691](http://www.ebuyer.com/product/107691)) 

It doesn't work "out the box", but only takes a few minutes to get working.



1) Copy the XP driver to a folder.

2) Install ndiswrapper via the package manager.

3) Use the "Wireless Network Drivers" graphical front-end of ndiswrapper to install the XP driver (netmw225.inf).

4) Configure your wireless connection as usual!

---

### Post by Nick8692 on 2008-03-12
yes, that looks good

any other suggestions?

---

### Post by Hightide on 2008-03-12
I agree with Wolfgen69, the Netgear WG111 v2 (usb dongle) works perfectly on my 2 ubuntu gutsy machines

regards

:)

---

### Post by forrestcupp on 2008-03-12
I bought a cheap Dynex pci card with an Atheros chipset from Best Buy and Ubuntu detected it and set it up automatically.  I didn't even have to go into Restricted Drivers Manager and enable anything.

---

### Post by Nick8692 on 2008-03-15
Yes, i was thinking of buying a card

any other recommendations?

---

### Post by Nick8692 on 2008-03-16
bump

---

### Post by Nick8692 on 2008-03-16
bump

---

### Post by Darkdelusions on 2008-03-16
I would reccomend using a PCI based card and one that is supported out of the box. Ndiswrapper is a great program however it can be temperamental at times or atleast it has been for me in the past

---

### Post by Keltar on 2008-03-16
Just picked up the netgear. it's v3 now. It didn't work out of the box. I am going to try some of the wrapper work and see what I can get.

---

### Post by Nick8692 on 2008-03-21
thats helpful to know

at the moment i think the Dynamode WLGI700S dongle would suit my needs, and you cant argue with the price:)

---

### Post by tuskenraider on 2008-03-21
i have a acer 9410z laptop.. built in wireless blew.. so went to newegg.com and purchased an edimax pc card for 16.99 plus shipping.  works fantastically!! right out of the box...  no issues no problems with the wpa network im running... im actually using it currently.. 
10 out of 10 times thats what i would buy. 
[http://www.newegg.com/Product/Product.aspx?Item=N82E16833315047](http://www.newegg.com/Product/Product.aspx?Item=N82E16833315047)

buy this one.. no dongles nothing to break....  
tusken

---

### Post by Nick8692 on 2008-03-28
good point

(bump)

---

### Post by ugm6hr on 2008-03-28
Is it a desktop?

PCI cards are less unpredictable than USB.

This one ([http://efficientpc.co.uk/components/wg311t/](http://efficientpc.co.uk/components/wg311t/)) is reliable for Ubuntu (Atheros chipset).

For laptops - Intel and Atheros cards are best.

---

### Post by Nick8692 on 2008-03-30
ahhh, cool

and yes, it is a desktop

---

### Post by ugm6hr on 2008-03-30
That card has only ever been available with a single Atheros chipset - so it is the safest bet for a desktop.

Other cards are a bit of a lottery, since successive versions change chipsets without notice.

---

