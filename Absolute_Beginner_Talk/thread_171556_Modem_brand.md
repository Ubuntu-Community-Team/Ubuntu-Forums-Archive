---
title: "Modem brand?"
date: 2006-05-06
forum: Absolute Beginner Talk
---

### Post by gRiMgRaVy014 on 2006-05-06
Please post some names of modem that work under Ubuntu Linux and are relativly easy to find/ cheap. My modem that came with my computer doesn't work under ubuntu for some reason :-x 

Thanks!

---

### Post by skippy81 on 2006-05-06
[http://www.tldp.org/HOWTO/Hardware-HOWTO/modems.html]("http://www.tldp.org/HOWTO/Hardware-HOWTO/modems.html")

A few specific working models are posted here.  It is possible to get most modems working under linux but winmodems (ie ones without their own controller chip) are harder to use.

---

### Post by johnc4510 on 2006-05-06
I had a trendnet TFM-560X serial modem that worked great, about $40. Whatever brand you get, get a serial modem, not a USB modem.

---

### Post by gRiMgRaVy014 on 2006-05-06
What about a PCI modem? Aren't serial modems had to find nowadays?

If I remember right the modme I have is a Lucet WinModem, probably why it doesn't work.

---

### Post by johnc4510 on 2006-05-06
Serial Modems aren't plentiful, but not hard to find either. Try going to trendnet's homepage and look for dealers in your area, or on the net, believe me  when I say this one works. I used it on breezy for a good 5 or 6 months before I got highspeed. Another plus is that it increased download speeds.

---

### Post by gRiMgRaVy014 on 2006-05-06
Do you still have that modem? I'll maybe buy it from you if you have paypal.

I'm looking on comp usa for the modem you used, they have it selling for $36

---

### Post by johnc4510 on 2006-05-06
I still have the modem, but I don't have paypal. If you wanted it I would be open to other suggestions

---

### Post by gigi1234 on 2006-05-06
My laptop has a Lucent Winmodem. You can get it to work by installing a driver yourself. If you want to investigate this solution look at [www.linmodems.org](www.linmodems.org). It is not the easiest thing in the world because you have to compile it from source. But it is not that bad either.

Also, I have a PCI Cardbus modem/ethernet card made by Xircom called "10/100 EtherJet Cardbus Ready Port Adapter With 56 K Modem" and it works "out of the box." You could probably get one on Ebay for about 10 bucks. It is slightly slower than the winmodem for some reason though. 

BTW, if your winmodem is the same Lucent modem I have, the driver is called "ltmodem-8.31b1.tar.gz". All you do is download this file (Google it) and compile it. To compile it you need GCC 3.4 and Build_Essential. The instructions are in the README  or the INSTALL documents.  

Good Luck.

---

### Post by gRiMgRaVy014 on 2006-05-07
john C: I've researched the modem you've mentioned online, all I've found was great reviews with no shortcomings of the modem mentioned, I think I might just go with that modem if I can find a cheap one online :p

---

### Post by akiro.yamamoto on 2006-05-07
Go to pricewatch.com and do a search for serial modems.
Or search for an Intel 537EP based modem. Intel provides linux drivers for this modem and I've had good results with it under Ubuntu 5.10. It should also be fairly cheap ( $10 ).
The serial modem I'm using is the [Best Data 56k Serial Modem.](http://www.gearxs.com/gearxs/product_info.php?products_id=3464)
Hope this info helps ;)

---

### Post by Mustard on 2006-05-07
Mines a local Australian brand of some kind, a Spirit Magnum.
[http://www.spiritmodems.com.au/](http://www.spiritmodems.com.au/)

---

### Post by Matchless on 2006-05-07
Hi. 
    External modems come in two types , connect to serial port or USB. If its a serial type you do not require any drivers. If its a USB type you will have to compile the sam as an internal winmodem. Your Spirit modem most probably uses a common chipset which determines which drivers are required. Go to the ubuntu wiki and search for Dialupmodem and there is a full explanation of the procedure. You can also install the modem in windows and do a modem query and maybe you could see what type or make of modem it actually is.
Good luck

---

