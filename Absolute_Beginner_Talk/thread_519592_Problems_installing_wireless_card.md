---
title: "Problems installing wireless card"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by -Morgoth- on 2007-08-07
I have some problems with getting my Broadcom Corp. Del Wireless 1390 WLAN Mini-PCI card on acer aspire 5103wlmi laptop to work. I have installed ndiswrapper 1.47 and downloaded some drivers i found on acer.com , but none of them seem to work. 
When i type :
sudo ndiswrapper -l   
i get the follow error: bcmwl5.inf invalid driver!

Anyone know whats wrong? Did i install the wrong driver?
Any help is appreciated...but Im a noob with linux btw ;)

---

### Post by Trash_Gordon on 2007-08-07
Well, what driver did you install exactly?

---

### Post by lgambett on 2007-08-07
First you should try to install the native Linux drivers for your PC. Try to uninstall NDISWRAPPER and install bcm43xx-fwcutter (sudo apt-get install bcm43xx-fwcutter) This package contains the firmware needed for your Broadcom card, that cannot be shipped with Ubuntu due to licensing policy. I think this will solve your problem, and this is better than Ndiswrapper.
If the native Linux drivers will not work you should search the drivers from the Ndiswrapper page,
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_0-9/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_0-9/)
as often the updated drivers from the producer site do not work.

---

### Post by PartisanEntity on 2007-08-07
I am not at my Ubuntu machine right now so I don't have access to some useful links. I used to use a Broadcom wireless card and I remember that the drivers consisted of two files, an *.inf and a *.sys file. They have to be in the same folder when you are installing them using ndiswrapper. Is that the case concerning the driver you are trying to install?

---

### Post by -Morgoth- on 2007-08-07
The drivers i first tried (from acer.com) were named "Broad 802BG_Broadcom_4_100_15_7" and "802BG_Broadcom_v4.10.40.0"

lgambett: I uninstalled ndiswrapper and installed those 2 things you mentioned. But then what next? Should the card work now? 

Thanks for the help  :)

---

