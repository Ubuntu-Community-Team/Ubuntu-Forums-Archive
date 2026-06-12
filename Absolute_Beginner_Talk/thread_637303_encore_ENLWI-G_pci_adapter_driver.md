---
title: "encore ENLWI-G pci adapter driver?"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by Techpenguin on 2007-12-10
hi everyone. as the title explains, could someone pleez tell me where to get such a driver for ubuntu? i would really appreciate it. and could you also pleeze tell me how to install it?:confused::confused::confused::confused:

---

### Post by spiderbatdad on 2007-12-10
try installing pcmcia-cs from synaptic then look in restricted driver manager

---

### Post by Techpenguin on 2007-12-10
where do i find this?

---

### Post by spiderbatdad on 2007-12-10
mmm. take a look at this thread:
[http://ubuntuforums.org/showthread.php?t=570061](http://ubuntuforums.org/showthread.php?t=570061)

---

### Post by Techpenguin on 2007-12-10
thxthxthxhtxthxthxthx:):):):):):):):)

---

### Post by spiderbatdad on 2007-12-10
do you know where to find synaptic package manager?

---

### Post by linuxn00ber on 2008-02-22
Hello. I am having a similar problem with Ubuntu 6.06 Dapper Drake not picking up my encore wireless ENLWI-G wireless card. 

First I had a Dlink wireless card in there and that card would work Ok right off of fresh install of Ubuntu but unfortunately my wireless network would have to be switched to using WEP which I dont want to do since I want to stick with WPA-PSK. This Encore card I have pulled out of an old machine will do the trick... if I can get it to work on this linux comp.

When I run lspci it shows it as a marvell technology group, ltd. 88w8335 [libertas] 802.11b/g wireless (rev 01)
but when I run iwconfig it doesn't show the wlan0 like it did with the dlink card I had. Going into system>administration>networking of course also only shows a modem and my 10/100 ethernet adapter.
Also, I have already tried Ndiswrapper installing the windows driver with no luck. it installs the driver and all but still wont see the card. The card I know is working cause it was pulled from an old windows machine where it was working great. Is this card not compatible with Ubuntu? If not, any suggestions for a card that support WPA-PSK with TKIP(bug free)?? Help is appreciated. I was thinking of getting a wireless bridge but man, that's more $$ thank my wife will let me spend for that easy fix. I am sick and tired of relying on my notebook to do ICS for this linux box. Plus I cant forward ports thru ICS without jumping thru a buncha hoops :(

---

### Post by linuxn00ber on 2008-02-23
Ok just an update to the previous post I made. I am now able to get the wireless card to activate and it is showing up in network properties. I followed the first few steps in this post:

[http://ubuntuforums.org/showthread.php?t=208088](http://ubuntuforums.org/showthread.php?t=208088)

right up to compiling the firmware. After I did this, I noticed that now ndiswrapper shows the device as active:no. I took the .sys and .inf files put them both into the same directory in one of my home folder locations and used the ndiswrapper. The card is now active and wants to go online, but unfortunately I am back at square one with the WEP issue. I cant seem to find anywhere to configure it to use WPA-PSK. Anyone have any suggestions from this point?

---

