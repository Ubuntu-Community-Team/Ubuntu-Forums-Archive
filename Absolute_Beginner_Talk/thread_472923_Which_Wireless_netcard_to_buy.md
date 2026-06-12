---
title: "Which Wireless netcard to buy"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by jimmi1311 on 2007-06-13
Hey

i have just installed Ubuntu 6.10 because I want to use LinuxMCE. I don't have a wireless netcard but I need one now but I don't know which one to buy??

I am not very familiar with linux but I have had some hardware problems before and I don't want that again. 

Any suggestion which card to buy??

BR
JImmi

---

### Post by dannyboy79 on 2007-06-13
netgear WG511T for sure. I have that and it works with dapper, edgy, and feisty out of the box! it has the atheros chipset so I believe anything with that similar chipset should work. according to my dmesg log, the ath_hal module, version 0.9.18.0, it works with these chipsets:
ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)

there are guides everywhere, just check some of the guides out that tell you how to make wireless work, and then just see what chipset or card they're referring to. I have to be honest, I just bought a Belkin USB wireless adapter, the F5D5070 and it doesn't work out of the box, you need to compile new serialmonkey drivers and I haven't done it yet as it's a spare machine. It doesn't even work in Gutsy yet but it may since gutsy is still in development. go to the wireless hardware guide for ubuntu and it should have wireless cards listed there, just gogle it.

---

### Post by Talon2 on 2007-06-13
> **jimmi1311 said:**
> 
i have just installed Ubuntu 6.10 because I want to use LinuxMCE. I don't have a wireless netcard but I need one now but I don't know which one to buy??

Any suggestion which card to buy??


Is this for a desktop or notebook?

---

### Post by jimmi1311 on 2007-06-13
It is for a desktop:-)

---

### Post by jcronkhite on 2007-06-13
For those who are going to be buying laptops, you may consider anything Intel Centrino as it too works out of the box.

---

### Post by dannyboy79 on 2007-06-13
check this out as I said: [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by H.E. Pennypacker on 2007-06-13
I direct you to:

[http://ubuntuforums.org/showpost.php?p=2710450&postcount=8](http://ubuntuforums.org/showpost.php?p=2710450&postcount=8)

---

### Post by Talon2 on 2007-06-13
> **jimmi1311 said:**
> It is for a desktop:-)

DLink DWL-2100AP:

[http://www.dlink.com/products/?pid=292](http://www.dlink.com/products/?pid=292)

This is an external wireless device that plugs into your your ethernet port.  No wireless drivers required.  The some what higher price is more than offset by the reduction in aggravation.  Ubuntu operates as if it is on a wired connection.  You control wireless via your browser.

Highly recommended.

---

