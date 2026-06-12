---
title: "Wireless?"
date: 2006-06-27
forum: Absolute Beginner Talk
---

### Post by LoDgEr on 2006-06-27
Ok since I installed Ubuntu I can't get through the internet. I have a Airlink Wireless PCI card and a Airlink Wireless Router. I activated my ra0 and configured it but i'm still having problems. What's wrong will I be able to get on the internet with Ubuntu? :-k

---

### Post by dmizer on 2006-06-27
what is the output of lspci?

---

### Post by Stromham on 2006-06-27
dose it have windows driver that need to be installed? is so you need ndiswrapper.

---

### Post by LoDgEr on 2006-06-28
It came with a disc to install, yes. How do I get that I can't access the internet with Ubuntu?

---

### Post by richbarna on 2006-06-28
Try this link for MadWifi :-
[http://madwifi.org/wiki/Compatibility#AirLink]("http://madwifi.org/wiki/Compatibility#AirLink")

---

### Post by dmizer on 2006-06-28
we really need more information before we can help you.  airlink makes several different models of wireless card (see here: [http://www.airlinkplus.com/wireless/wireless.htm](http://www.airlinkplus.com/wireless/wireless.htm) ) ... we have no way of knowing what your card is.

save the output of lspci to a text file, dump it on a floppy or usb drive and cary it over to windows.

according to the wiki: [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported) there is only one airlink card that has been tested, and it should work out of the box.  since yours does not, we need to figure out which one it is.

if you can't figure out how to transfer lspci output to your windows so you can paste it here, look at the output yourself and write down the relevant information you find regarding your wireless card.

---

### Post by LoDgEr on 2006-06-28
I fixed it. Thanks for the help!

---

