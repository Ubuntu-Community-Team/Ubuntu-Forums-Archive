---
title: "Wireless networking setup"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by Jim Rogers on 2007-01-23
I have tried to follow the threads I could find here, but I must be missing something. I am completely new to UBUNU and will need some handholding to get this working. So if some kind soul could talk me thru this I would appreciate it.

My Linksys wireless adapter is a WMP45G.. I tried setting up both wireless networks that appear in the ubuntu networking screen, but neither works.

Any and all help appreciated.

---

### Post by stephentyler20 on 2007-01-23
Having just done this recently, I have two pieces of advice:

1. There is a program whose name I can't remember that allows you to install the Windows driver for your Wifi card on Linux... do a search of the archives and you can find the name of the program, which you download from synaptics (instructions are also searchable). Then download the windows driver for your network card, and install with the program (Which is very easy).

2. Download, via Add/Remove Programs, a program called Wifi Radar. This is basically a replica of the Windows Wifi finder system, and is very simple and intuitive to use.

---

### Post by mikewhatever on 2007-01-23
Start with this guide [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide) to check if your wireless card is detected.

---

### Post by Jim Rogers on 2007-01-25
Thank you all for all suggestions.

Worked all day today and have successfully, it seems, compile the Ralink driver for their RT61 chip set.

This may be a career thing but time is of no consequence, at least I am learning something.

They say it is good for staving off dementia....

---

### Post by Jim Rogers on 2007-01-29
SOLVED

Linux drivers from ralinktech website were compiled.

an entry was made in /etc/network/interface

     auto ra0
     iface ra0 inet dhcp

to run dhclient on boot.


SOLVED

---

