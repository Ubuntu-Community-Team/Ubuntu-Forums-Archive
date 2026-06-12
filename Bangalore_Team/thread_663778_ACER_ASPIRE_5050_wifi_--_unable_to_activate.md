---
title: "ACER ASPIRE 5050 wifi -- unable to activate"
date: 2008-01-10
forum: Bangalore Team
---

### Post by nautaforever on 2008-01-10
its been about 2 months since i changed over to ubuntu. everythings going on fine got all drivers to work except for my wifi.

my laptop specs are :

ACER ASPIRE 5050
AMD Turion 64x2 1.8Ghz
Atheros 802.11b/g wireless lan

its the Atheros thats giving me the problem. i'm unable to install the driver for it. tried to use Ndiswrapper but that dint help, tried to use Madwifi drivers for the card, but of no use. i'm using Gusty 7.04 version my kernel is 2.6.22-14 if its of any help

any suggestion will be greatly appreciated

UBUNTU ADDICT

---

### Post by twright on 2008-01-10
ndiswrapper is probable the best way

try looking here:
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_c-f/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_c-f/)

you could also try this in terminal
```
sudo -i
echo ndiswrapper >> /etc/modules
```

---

### Post by aswinms on 2008-05-11
> **nautaforever said:**
> its been about 2 months since i changed over to ubuntu. everythings going on fine got all drivers to work except for my wifi.

my laptop specs are :

ACER ASPIRE 5050
AMD Turion 64x2 1.8Ghz
Atheros 802.11b/g wireless lan

its the Atheros thats giving me the problem. i'm unable to install the driver for it. tried to use Ndiswrapper but that dint help, tried to use Madwifi drivers for the card, but of no use. i'm using Gusty 7.04 version my kernel is 2.6.22-14 if its of any help

any suggestion will be greatly appreciated

UBUNTU ADDICT

I have the same problem and unfortunately there is no solid solution as of now!(at least for Gutsy!) I have been trying to get this sorted out for he past one year, I had read in an Ubuntu documentation site that the Atheros card has been blacklisted, ndiswrapper may give you temporary solutions but it doesn't work most of the times! I was hoping Hardy might sort out these problems but Hardy was too heavy for my machine(Acer Aspire 5573ZNWXMi) and I had to revert to Gutsy! I use a cable and plug it in all the time :(

---

### Post by bhavi on 2008-06-13
> **aswinms said:**
> I have the same problem and unfortunately there is no solid solution as of now!(at least for Gutsy!) I have been trying to get this sorted out for he past one year, I had read in an Ubuntu documentation site that the Atheros card has been blacklisted, ndiswrapper may give you temporary solutions but it doesn't work most of the times! I was hoping Hardy might sort out these problems but Hardy was too heavy for my machine(Acer Aspire 5573ZNWXMi) and I had to revert to Gutsy! I use a cable and plug it in all the time :(
Ashwin try wicd 

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

[http://wicd.sourceforge.net/wiki/doku.php?id=faq](http://wicd.sourceforge.net/wiki/doku.php?id=faq)

---

### Post by parth shah on 2008-11-06
e
> **nautaforever said:**
> its been about 2 months since i changed over to ubuntu. everythings going on fine got all drivers to work except for my wifi.

my laptop specs are :

ACER ASPIRE 5050
AMD Turion 64x2 1.8Ghz
Atheros 802.11b/g wireless lan

its the Atheros thats giving me the problem. i'm unable to install the driver for it. tried to use Ndiswrapper but that dint help, tried to use Madwifi drivers for the card, but of no use. i'm using Gusty 7.04 version my kernel is 2.6.22-14 if its of any help pls send me drivers


any suggestion will be greatly appreciated

UBUNTU ADDICT

---

### Post by nautaforever on 2009-06-23
the problem solved itself after i installed versions that came after Gusty.

---

### Post by myacer on 2009-06-30
Where i can download the acer aspire 5050 battery driver?
I  got the acer 5050 battery at [http://www.sales-battery.com/laptop-batteries/acer-aspire-5050.htm](http://www.sales-battery.com/laptop-batteries/acer-aspire-5050.htm) but it does not work well, my friend told me to download new drivers.

---

### Post by aiser on 2009-12-01
:confused:

---

