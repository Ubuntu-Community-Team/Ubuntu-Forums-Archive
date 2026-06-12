---
title: "Wireless card compatibility"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by C!pheR on 2008-03-29
I will shortly be installing Ubuntu on another computer. The owner would like to switch to WiFi instead of Ethernet. I've read that there can be problems getting Linux o recognise and use wireless cards out of the box. Is there any wireless PCI cards that are compatible with Ubuntu that doesn't require too much fiddling about to configure?

---

### Post by FuturePilot on 2008-03-29
Intel wireless cards usually work out of the box. Also any cards that use the Atheros chipset usually work out of the box as well using the Madwifi driver. I have a laptop with an Intel 3945ABG and a laptop with a Netgear WGT11T card which uses the Atheros chipset. Both cards worked out of the box.

---

### Post by Tom--d on 2008-03-29
ndiswrapper uses Windows drivers to run the wireless drivers. 

I'm using it now and it works perfectaly :D

---

### Post by FuturePilot on 2008-03-29
That's great, but "ndiswrapper" and "not too much fiddling" usually don't fit in the same sentence too well. ;)

---

### Post by C!pheR on 2008-04-03
Thats pretty much what I was thinking, thanks guys. :)

---

### Post by Helios1276 on 2008-04-03
ndiswrapper THAT much work?? I REALLY want my wireless back :(

---

### Post by Xiong Chiamiov on 2008-04-03
I was using [an Edimax card]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833315041") which was a pain to get working on Windows, but worked out-of-the-box on Linux.

---

### Post by ugm6hr on 2008-04-03
This PCI card is a safe bet.  

[http://efficientpc.co.uk/components/wg311t/](http://efficientpc.co.uk/components/wg311t/)

It has only ever been available in one version with Atheros chipset.

It works out-of-the-box (Ubuntu will ask you if you want to install the Restricted Driver).

---

### Post by ConorBuzz on 2008-04-03
STAY AWAY FROM BROADCOMM

sorry for shouting but they are a real Pain 

look at the HCL  for ubuntu 

and use  ndiswrapper to install the  drivers from windows . 

There are loads of links on how to install with ndiswrapper  


& 

STAY AWAY FROM BROADCOM 

lol

---

### Post by stalkingwolf on 2008-04-03
While being a tad old this site is a good resource for checking compatibility of 
wireless cards.

[http://linux-wless.passys.nl/](http://linux-wless.passys.nl/)

---

### Post by Oak37 on 2008-04-03
The community documentation has a good [list]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported"). Apart from that, my own personal recommendation is the WPN311 by Netgear. Never had any issues with it, worked right out of the box.
I also had a Belkin F5D7000 which I did manage to get working through ndiswrapper for a while but I would not recommend it, especially as it went under infinite revisions and changed chipsets without telling anyone [-(

---

### Post by Jozza The Wick on 2008-05-31
I can also recommend the Netgear WG511T (not the regular WG511). Ordered from Staples, it just arrived today. Pulled out old card, plugged in this one. Worked immediately. Browsed to router, re-enabled WPA. Was asked for password, and these forums are the first place I browsed to to tell everyone!

Am running 7.10 on a Dell Inspiron 8100, if anyone's interested...

---

