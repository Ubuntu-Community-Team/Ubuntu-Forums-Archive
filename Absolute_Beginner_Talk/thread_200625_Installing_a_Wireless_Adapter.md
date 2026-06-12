---
title: "Installing a Wireless Adapter"
date: 2006-06-20
forum: Absolute Beginner Talk
---

### Post by HarrisonHopkins on 2006-06-20
Alright, I have a SMC networks EZ-connect G Wireless USB adapter. To install it on my Xubuntu system, do I use the disk that came with it, or do I need to get a generic driver?

---

### Post by vg3 on 2006-06-20
The drivers on the disk are probably for windows and will not work with Xubuntu.

---

### Post by HarrisonHopkins on 2006-06-20
So, do I need to look for linux ones, get a generic one, or wait for one?

---

### Post by cidica on 2006-06-20
My advice would be check out the package linux-wlan (it came on my iso of drapper drake). Heres a link to the suported usb devices --> [http://at76c503a.berlios.de/devices.html]("http://at76c503a.berlios.de/devices.html")also  Also if linux-wlan doesnt support your driver.. check out ndiswrapper. It allows you to use windows drivers. 
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List")
is a good start if linux-wan package doesnt support your card/usbdevice. It has lots of cards that have all been tested with ndiswrapper.  Hope this helps. Wireless was a pain in the butt to set up for me. ](*,)  Finally got it working with ndiswrapper.

---

