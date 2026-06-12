---
title: "general help and internet conecting"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by chuck88 on 2008-02-03
I am jonny come latley to linux and to computers in general. In other words my knowledge is a lot like swiss cheese solid in some areas but with random gaping holes in others. I cannot conect to the internet. firefox gives the standard cannot find serer page, but offers no help to solve the problem. The help pages are more for how to navagate the internet not how to get on initially and the getting started horse needs an internet connection in the first place to get started. In short if someone could direct me to a website or book (s) that asume absolutely zero knowledge about computers on the part of the reader (no acronyms and computer words without a glossary) that would be very helpful. Also how do I connect to the internet, it was working before7.10? Tired of being tied to a windows machine.

thanks for your time
Chuck

---

### Post by jan quark on 2008-02-03
try this sites to get started

[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)
[https://help.ubuntu.com/community/InternetHowto](https://help.ubuntu.com/community/InternetHowto)

---

### Post by billgoldberg on 2008-02-03
Well, if you are using an ethernet cable to connect to the internet everything will work in a second.

If you are using a wireless pci card or usb adapter things could get a bit tricky due to manufactures not writing any linux drivers.

A couple of things you could try:

1. Go to "system -> administration -> restriced drivers management" and look if you're wireless card is in there. If it is, enable it and it should work.

2. The iternet icon on the top panel, press it and look if it sees any wireless networks. Select yours and enter a your wpa/wep key. If the key doesn't work use ndiswrapper or disable your wireless encryption.

3. Use a different program to connect to the internet. Instead of using "network manager".
I used WICD before and it works a bit better sometimes.

Download it here:
[https://sourceforge.net/project/showfiles.php?group_id=194573&package_id=229460&release_id=565671](https://sourceforge.net/project/showfiles.php?group_id=194573&package_id=229460&release_id=565671)

(download the .deb package, and double click it to install), you will have to remove "network-manager using synaptic (sytem -> administration), to reinstall network manager go to synaptic, insert your ubuntu cd, search for network manager and reinstall it.)

4.I mentioned ndiswrapper before, so post a question in the correct subforum for help with that.

5. Buy and wireless usb adapter (those go for 30 bucks these days) that is fully linux compatible. 
[URL="https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported#head-603c9481d6c6288b6b674cc50132d21f6d539c53"]Click
 here[/URL] for that list.

Hope I helped.

---

### Post by chuck88 on 2008-02-06
alright, here's my set up. I have a windows desktop which conects to a cable modem: Motorola SURFboard® Cable Modem SB4200. Then an eithernet cord to the cpu. When I unplug the eithernet cord and plug it into my ubuntu laptop, I can not get onto the internet. I don't know if it's the kind of modem, or if I need to do something on the laptop to make it work.

thank you kindly
 
chuck

---

