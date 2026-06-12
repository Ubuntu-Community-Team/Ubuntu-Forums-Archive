---
title: "Wireless Problem"
date: 2006-10-13
forum: Absolute Beginner Talk
---

### Post by Alvar on 2006-10-13
Hi, I'v got a problem with my wireless. This is my first time using ubuntu. When I sign on to ubuntu I have no wireless, In windows, all I had to do was press and hold function key and the wireless key(was F2). But when I try that on ubuntu the wireless sign doesnt't turn on. I tried activating my wireless by:
System-->Admin-->Networks, then activate wireless, but nothing happens. Please help me

---

### Post by thornomad on 2006-10-13
Probably folks could use some more info about your Wireless setup -- is it a card or internal ?  Do you know the specs ?

---

### Post by Alvar on 2006-10-13
It is an internal, idunno how to get specs, mby u can tell me how. I'm using windows right now.

---

### Post by Alvar on 2006-10-13
It says Broadcom 802.11g Network adapter
Location: PCI bus 1, device 9, function 0

---

### Post by thornomad on 2006-10-13
I will have to defer to someone with more experience than me; the first wireless card I had with my laptop wasn't compatible with Ubuntu and I went and bought (on eBay) a D-Link 650+ card which works the minute it was plugged in.  Was disappointed to have to a buy another one, but for $12, was an easy fix.

Search the internet for drivers for that version; certainly you are not the first person to have that chipset and trying to use Ubuntu/Linux.

---

### Post by Alvar on 2006-10-13
Is this card you talk about like a usb plugin? or do i need to open up my laptop to put this in??

---

### Post by agc on 2006-10-13
If you boot back into ubuntu, open a console, and type:

```
lspci | grep Broadcom
```

then post the response here,
we can then figure out the details of the problem.

(if you are not that familiar with using the console/terminal,
dont worry to much about the code :) )

---

### Post by crimesaucer on 2006-10-13
Hello, I don't mean to hi-jack this thread, but I'm trying to configure my internal wifi card for my HP Pavilion dv4230us celeron 910gml chip set.

my wireless card is: 54g™ 802.11b/g WLAN with 125HSM / SpeedBooster support

is there a page for configuring computer hardware with xubuntu/ubuntu...

thanks,
-c.

---

