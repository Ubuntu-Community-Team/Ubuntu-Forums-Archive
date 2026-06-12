---
title: "Best wireless USB adapter For Feisty Fawn"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by jlambeth1 on 2007-05-07
I bought a Belkin wireless USB adapter to hook a second computer into my network but was looking to avoid using ndiswrapper or other methods to get it working.  I just want to plug and play if there is one out there that will do that.  Does anyone have any wireless USB adapter that they recommend that will work right out of the box?

---

### Post by overdrank on 2007-05-07
> **jlambeth1 said:**
> I bought a Belkin wireless USB adapter to hook a second computer into my network but was looking to avoid using ndiswrapper or other methods to get it working.  I just want to plug and play if there is one out there that will do that.  Does anyone have any wireless USB adapter that they recommend that will work right out of the box?

Hi this link may help.
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)
Good luck!:guitar:

---

### Post by jlambeth1 on 2007-05-07
Thanks for the link.  I already looked through the list earlier today and did not see any that were available in the local Best Buy, Circuit City, etc.  I see several that say yes but need some configuring to work.  I just wanted to plug it in and go.  I got my machine up and running after countless hours researching my problems and did not feel like putting in tons more time getting my son's machine running when he just wants to goof around with Ubuntu and the blender program.

---

### Post by bsell on 2007-05-07
I use a Netgear wireless USB adaptor. It's PnP. Just Works (TM) out of the box.

---

### Post by Bachstelze on 2007-05-07
I have an Asus one with a Ralink chipset (don't have the exact specs in mind right now) which Just Works (TM) in Linux *and* in FreeBSD (the FBSD compatibility being the main reason I bought it since my built-in Intel work perfectly in Linux).

---

### Post by jlambeth1 on 2007-05-07
Thanks for the suggestions.  Bsell, do you by chance know the model number of your Netgear adapter?

---

### Post by bsell on 2007-05-07
> **jlambeth1 said:**
> Thanks for the suggestions.  Bsell, do you by chance know the model number of your Netgear adapter?

WG 111v2

---

### Post by jlambeth1 on 2007-05-07
Thanks, I'll give that one a try.

---

### Post by Tarrasque on 2007-05-08
> **bsell said:**
> WG 111v2

So, could someone update the list on [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported) ?

The card's not listed there.

I think that kind of charts are the best help a newbie to Linux can use. :D

---

### Post by eiapoce on 2007-05-10
Hi guys. I can tell what's not working out of the box.

I tried those usb wireless adapters:

SITECOM Model WL-113 V1 002 - This one gets recognised, gives signal levels in the network manager but cannot connect to a WEP 64bit protected AP - It does not work in kismet

3COM Model 3CRUSB10075 - This one is not recognized in Network Manager, but it works in Kismet 

USROBOTICS Model USR805423 - Not recognized in NetWork Manager, couldn't find a way to make it work in KISMET

So long... this list is depressing, also the integrated chipset (Ralink RT2500) does not work. I am left with no wireless connection. 

Enrico

---

### Post by andykrueger on 2007-05-10
HymnToLife, I would like to know what model adaptor you're using.  

All the recommended adaptors I've seen so far seem to be wireless-B standard.  I'm hoping to find one that's G or faster that will just plug and play in Feisty.

---

### Post by r0ger on 2007-06-09
I use a USR 805423 wireless USB adaptor. It works! Support for installation procedure in italian language here [http://www.viti.tv/modules/news/article.php?storyid=53]("http://www.viti.tv/modules/news/article.php?storyid=53")

Ciao!

---

### Post by Drifter on 2007-06-09
I don't thank there is a best wireless for fiesty fawn

---

### Post by aberadam on 2007-06-09
I had the same problems as the OP.  

[I bought the USB stick at the bottom of this page]("http://www.linuxemporium.co.uk/products/wireless/")

Why?  Because they send a disk with it that contains working drivers for it which sorts out the problem of where/how to get the drivers onto Ubuntu and will help you via email.  I've exchanged 16 emails with them!  Great guys and with their help I got it working.

---

### Post by aberadam on 2007-06-09
It was not working out of the box but all you have to do is unpack a file from the CD to your computer  and then run a script they've written that's in that file.  

I needed help just to do that but got it working and I'm a complete Linux newbie.

---

