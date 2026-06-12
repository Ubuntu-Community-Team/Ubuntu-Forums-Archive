---
title: "Need Help Setting up Wi-Fi"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by htmlguy on 2007-11-12
I just downloaded xbuntu today and love it. My only problem is that I can't get connected to the internet. I use a Linksys WUSB54GS v2. Do I have to install a driver or something or can I get to work by just changeing some settings? If the later which settings do I change?

[http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1169083632250&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=3225039789B02](http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1169083632250&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=3225039789B02)

---

### Post by chlorinekid on 2007-11-12
go to system > administration > network and check that your wireless card is being detected. the link above appears to be your router. which wireless device do you use?

---

### Post by houstonbofh on 2007-11-12
Your card is not natively supported in Linux.  You can try ndiswrapper, and may have some positive results.  Some have reported success.

However...

Let me start with **this is only my opinion, not fact.** :)  Some WiFi cards are a pain in the *** under any OS.  And some can only be made to work in Linux by sacrificing a young goat, or some such.  Others can work easily, but have flaky performance, or are not supported by all the tools (WPA supplicant, Network Manager, kismet, hibernation...) or just do not function well with some apps.  I value my sanity more than this!

Additionally, why support vendors that do not support us?  I just have a problem giving money to someone who does not value me as a customer.  So, some links...

Philosophy
[http://www.fsf.org/resources/hw/net/wireless/cards.html](http://www.fsf.org/resources/hw/net/wireless/cards.html) (note that HP/Compaq also blacklist minipci)
There are other well supported cards (Atheros and the like) but they have closed firmware.  I figure if you are buying a card anyway, buy an open one.

A list
[http://ralink.rapla.net/](http://ralink.rapla.net/)

Every time I buy a card it is on the list above.  Every time it just works out of the box with full functionality.  It runs native in Linux which means less overhead, and better speeds.  I am currently connected with this card. [http://www.airlink101.com/products/awlc5025.html](http://www.airlink101.com/products/awlc5025.html)  Setup was limited to inserting the card. Done.

---

