---
title: "not work netgear ?"
date: 2006-12-22
forum: Absolute Beginner Talk
---

### Post by Janoubie on 2006-12-22
hi all ...  I'm really need help ... I'm new in ubuntu .. i love it really 
but when I install in my laptop everything change ... I have 
toshiba satellite A40-261
no wireless incloud .. I have wireless dsl connection by speedtouch 585 ..
i bought netgear wireless card WG511 v2 ..made in china 
before i search in ubuntu giude and i look it's possible this card work in ubuntu 
i follow some topic here in forum but nothing i'm new in ubuntu .. i'm try and try not work what can I do .. if this part not good tell me to reback to store only one day ..
some topic that not works
[http://www.ubuntuforums.org/showthread.php?t=76804](http://www.ubuntuforums.org/showthread.php?t=76804)

---

### Post by dbbolton on 2006-12-22
what kind of drivers do you have installed ?

---

### Post by MrKlean on 2006-12-22
There's a good article in Tuxmag... here's the url...[http://www.tuxmagazine.com/node/1000167](http://www.tuxmagazine.com/node/1000167).  I just used it and it worked for me on a WG311.v3.  I had to manually associate it tho..explained in the article..

---

### Post by Janoubie on 2006-12-22
thx for replay and help me ... i'm re back to store becouse my friend send me this page it says linux not work with it 
[http://linux-wless.passys.nl/query_part.php?brandname=Netgear&zoek=Show](http://linux-wless.passys.nl/query_part.php?brandname=Netgear&zoek=Show)

then i buy linksys WPC54G 
but still need help

---

### Post by jacksonz123z on 2006-12-27
This card can use two different drivers.  I have a card with the Marvel driver, some cards have Prism drivers.  Both cards will work, my card with the Marvel driver works well with ndiswrapper.

---

### Post by seeklinux on 2006-12-29
I have netgear  WG511V2 also and it works fine with ndiswrapper. You first need to install ndiswrapper (I have version 1.18-1ubuntu2 of both ndiswrapper-common and ndiswrapper-utils) using synaptic.  You also need to have your netgear disk handy for the device drivers.  I would recommend copying the driver files to your hard disk or a flash drive, at least temporarily. The steps I took once I had ndiswrapper installed were:

[B]sudo ndiswrapper -i *path_to_driver_files*/WG511v2.INF
sudo ndiswrapper -m
sudo modprobe ndiswrapper
sudo ndiswrapper -l[/B]

When you issue the third command the light on the card should come on. The last command simply displays information. I get the following:

[B]Installed drivers:
wg511v2         driver installed, hardware present[/B]

If you want to use WPA you may need newer drivers from the Netgear site. At least I did.

---

