---
title: "2 Wireless Cards"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by fmbugdadi on 2008-01-04
I recently bought a new wireless card that fits into PCMCIA slot. Now ubuntu, sees both of them, however, it defualts to the built in card when connecting to my wireless network. I have to disconnect from the network and manually connect with the new card.  How do I disable the built in card, so that Ubuntu will automatically connect with the new card? Thanks....

---

### Post by kestrel1 on 2008-01-04
Why do you want to use the PC card in favour of the built in wireless?
You may be able to disable the built in wireless by going in to the BIOS. There will probably be an option to disable it.

---

### Post by fmbugdadi on 2008-01-04
I want to disable it because it only supports 802.11/a/b. Has no "g" support. This is an older laptop, that was around before "g" band was. Thanks for the info, I will give that a shot.

---

### Post by Paulmd on 2008-01-04
> **fmbugdadi said:**
> I want to disable it because it only supports 802.11/a/b. Has no "g" support. This is an older laptop, that was around before "g" band was. Thanks for the info, I will give that a shot.

On most models of laptop, you can remove the built in card.  It's either under a panel on the bottom of the laptop (easy). Or under the keyboard, which isn't as easy.

If you let me know what make and model laptop you have, I can probably find a service manual, or disassembly guide.

---

### Post by fmbugdadi on 2008-01-04
This is an IBM Thinkpad G40 model 2389. I tried going into the bios, and found 8 pci devices without descriptions, so, I disabled one at a time, however, it saw the wireless card everytime. So unless there is a device manager, my only option will probably be removal.

---

### Post by Paulmd on 2008-01-04
> **fmbugdadi said:**
> This is an IBM Thinkpad G40 model 2389. I tried going into the bios, and found 8 pci devices without descriptions, so, I disabled one at a time, however, it saw the wireless card everytime. So unless there is a device manager, my only option will probably be removal.

IBM was a good choice, from a service point of view. 


[http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-51461](http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-51461)

Here's how to remove the keyboard:

[http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-52426](http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-52426)

---

### Post by warrior24 on 2008-01-04
The hp laptops ive seen have a button that turns the internal wifi on. Somewhere on the laptop keyboard usually.

---

### Post by kestrel1 on 2008-01-05
Not sure that the older IBM laptops had the option to turn the WiFi off.
As mentioned above, removal would be tour best option. You may even be able to get a replacement card that has wireless G enabled that may work, but as you already have the PC card it probably isn't worth it.

---

### Post by ugm6hr on 2008-01-05
> **kestrel1 said:**
> Not sure that the older IBM laptops had the option to turn the WiFi off.
As mentioned above, removal would be tour best option. You may even be able to get a replacement card that has wireless G enabled that may work, but as you already have the PC card it probably isn't worth it.

mini-PCI a/b/g cards are available on ebay for under £15.  Atheros and Intel cards are best supported by Linux.  Much slicker than having a PCMCIA card stuck out the side of the laptop.

---

