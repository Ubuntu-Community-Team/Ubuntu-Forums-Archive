---
title: "Toshiba Notebook WiFi problems"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by ncwitte on 2007-02-03
Hello, and thanks for your help.  I have two Toshiba Satellite 1955-S803 notebooks.  My IT dude set one of them up with Ubuntu.  That machine has the stock "b" internal wireless card and it connected to WiFi no problem.  I then switched the hard drive from one machine to the other.  Everything is running fine on the second machine, but the WiFi will not connect.  This machine is pretty much identical to the first except that it has a "g" internal WiFi card.  I can see the wireless conection in the Networking menu; I have inputed the SSID and WEP key correctly, and the wireless card is turned on.  Any suggestions?

Also, is there a feature in Ubuntu that detects wireless networks and displays signal strength, connection status?

Thanks in advance for your help on a cold Michigan morning.

Norm

---

### Post by igknighted on 2007-02-03
Wireless 'b' and 'g' don't really make to much difference... it all depends on the specific chip inside the card.  (i.e., I have a belkin 'g' card, but the chip is an aetheros chip).  Your card may have a native linux driver as you say it is recognized, however it may not, which might require the NDISwrapper, which provides an intermediate layer that allows the use of windows WiFi drivers.

---

### Post by ncwitte on 2007-02-03
Is it possible for the card to be recognized and not have a Linux driver?

---

