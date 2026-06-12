---
title: "Network problems. Please help."
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by pankirk on 2008-03-18
I have a wireless PCI card for my computer (linksys WMP54G) and It works fine with the live CD, no problems at all, I can go for hours on end using the internet on the live CD. But when I switch over to my actual ubuntu installation, my interent connection randomly stops being connected to the internet, and the only way to make it connect again is to reboot my computer and start it all up again. I am wondering, maybe is there a PCI version for my driver and Ubuntu seemed to install the wrong version? Or what is going wrong here... Why does the live CD work fine on the internet, but on my real installation the internet only work for about 10 minutes and then it dies. Please help! Thanks in advance!

EDIT: I just searched for "wireless pci" in synaptic and linux-wlan-ng came up. I installed it, hopefully something good will come out of this...

---

### Post by pankirk on 2008-03-18
here is my hardware:

[html]  *-network               
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: wmaster0
       version: 00
       serial: 00:18:f8:a7:fd:8a
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci ip=192.168.1.104 latency=32 module=rt61pci multicast=yes wireless=IEEE 802.11g
[/html]

---

### Post by pankirk on 2008-03-19
Also, doy ou think it hurts my network connection drivers when i just hold the power button to shut off my pc? I do that sometimes...

---

### Post by pankirk on 2008-03-19
Any help from anyone would be great. I hope nobody gets offended that I double posted, but I had to d o it in order so that my thread doesnt go down without an answer...

---

### Post by pankirk on 2008-03-19
Hello.

---

### Post by dsauxier on 2008-03-20
The next time it drops the connection, can you run the following commands, save the output to a file, and then post it after you reboot ? 

That information should be useful if one of the guru's reads this thread.

sudo lspci

dmesg | tail -75

---

