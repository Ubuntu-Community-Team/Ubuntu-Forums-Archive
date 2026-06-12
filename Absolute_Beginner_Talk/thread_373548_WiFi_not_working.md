---
title: "WiFi not working"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by SamTyson92 on 2007-03-01
Im really tempted to install ubuntu but it wont work with my wireless network card its a:
Atheros AR5006EG Wireless Network Card

And if I can't use wifi Im stuck with no internet as Im normally upstairs and the access point is downstairs and so really I need to be able to use wifi.

But Ubuntu said it wouldnt work when I started ubuntu.
Is there anyway to make it work?
And will Ubuntu fit on a USB Drive with 6.5GB space left?

---

### Post by PartisanEntity on 2007-03-01
Which version of Ubuntu are you using/testing?

If you have the driver files, you can use ndiswrapper to install them.

If your wifi network uses wpa encryption you can use wpasupplicant and network manager to access it.

I know that the Atheros worked out of the box on a friends laptop when I installed Ubuntu 6.06 on it for them.

---

### Post by SamTyson92 on 2007-03-01
Well ive been trying 6.06 and the newest version.

---

### Post by PartisanEntity on 2007-03-02
As I pointed out earlier, we need more information.

Are you connecting to an encrypted network, if yes which?
Do you have the correct driver files for your network card?
Do you have wpasupplicant and network manager installed correctly?

---

### Post by SamTyson92 on 2007-03-02
Yes is an encyrted netowork, I have the drivers but as ive not acutally install ubuntu yet will that be the problem also the driver is a .exe which dosent work on ubuntu.

---

### Post by PartisanEntity on 2007-03-02
Based on my experience it was never possible (for me) to set up wifi on 6.06 without being physically connected to ethernet cable *first*.

However in 6.10 (edgy) it is possible to set up the wifi connection without ethernet as long as you download 5 files first (namely: network-manager, network-manager-gnome, libnl1-pre6, libnm-util0 and dhcdbd) You would need to download these files from [http://packages.ubuntu.com/](http://packages.ubuntu.com/) (always making sure you are downloading packages for edgy).

Good luck.

---

### Post by ellis rowell on 2007-03-02
"Well ive been trying 6.06 and the newest version."

I tried to install v6.10 several times on my Laptop but each time it fell over at 15% on the final scale. I then tried v6.06 and it installed OK. Haven't got the WLAN working yet, I use an ethernet cable.

My biggest problem is printer drivers. I bought Turboprint in order to get drivers for my printers (Canon Pixma IP1600, Epson Stylus C680 and a Minolta Magicolor 2400W laser), but CUPS keeps overiding it and although the Epson works OK, neither of the other two do. 

How can I get Turboprint working without CUPS messing it up.

---

### Post by PartisanEntity on 2007-03-02
Perhaps it would be better to start a new thread about your printer problem, otherwise you will mess up this members wifi problem thread.

---

