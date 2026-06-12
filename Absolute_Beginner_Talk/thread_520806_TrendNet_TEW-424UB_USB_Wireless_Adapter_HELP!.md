---
title: "TrendNet TEW-424UB USB Wireless Adapter HELP!"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by jkarns on 2007-08-08
I am very new to Linux/Ubuntu. I have a Trendnet TEW-424UB USB Wireless Adapter. I found a wireless compatibility page on the Ubuntu website, and it says this model, "Works perfectly with NdisWrapper in Dapper, Edgy, and Feisty. Drivers provided on the CD worked fine."

Problem is...I don't know what this NdisWrapper is. Does anyone have a step by step on how to get this adapter working? I am have Fiesty loaded, on a Dell D800 Latitude with a 1.8 PentIII and 512mb Ram. 

Please HELP!

---

### Post by oilchangeguy on 2007-08-08
[http://en.wikipedia.org/wiki/NdisWrapper](http://en.wikipedia.org/wiki/NdisWrapper)

---

### Post by Steve1961 on 2007-08-08
First you need to identify the chipset.  Plug it in and type 

lsusb

from the terminal.  Post the output here.

---

### Post by jkarns on 2007-08-08
This is the output I get in lsusb\


jeremy@laptop:~$ lsusb
Bus 004 Device 003: ID 0bda:8189 Realtek Semiconductor Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

---

### Post by Steve1961 on 2007-08-09
OK you have a realtek chip in teh card.  See this post for drivers:

See this post for details:

[http://ubuntuforums.org/showthread.php?t=383504&highlight=TEW-424UB](http://ubuntuforums.org/showthread.php?t=383504&highlight=TEW-424UB)

Then search for instructions for installing ndiswrapper

---

