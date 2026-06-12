---
title: "Wireless setup for old laptop"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by ubername on 2007-06-28
Hi

I have an old dell laptop which does not have a wired network (ethernet) socket. However it does have a wireless card (broadcom) which worked fine under win98SE. I have trashed win98 and got ubuntu working, but I can't get the wireless working. During the ubuntu install I got a message along the lines of ' your DHCP server is not working or responding slowly' so I selected 'don't configure network at this time' (or similar).

Any clues? The lights on my wireless card are alive,  I have searched a bit but the answers seem all to depend on having a wired network connection to fall back on (by suggesting sudo apt-get this or that, which I can't do, as I have no network).

TIA

P.S. obviously I have another computer which I can use to connect to networks, so I can post this!

---

### Post by shearn89 on 2007-06-28
Hopefully you won't have to install anything to follow the following howtos: if you do, get the web address of the universe repo by looking at "/etc/apt/sources.list", and download the package to a ram pen or something...

1. Check [here]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported") for info on your card.

2. If it says something about ndiswrapper, use [this]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") howto.

---

### Post by ugm6hr on 2007-06-28
> **ubername said:**
> Any clues? The lights on my wireless card are alive,  I have searched a bit but the answers seem all to depend on having a wired network connection to fall back on (by suggesting sudo apt-get this or that, which I can't do, as I have no network).

Maybe post the output of *lspci* (in Terminal) - to inform us of your exact chipset (look for Ethernet / Network controller).

And post the links of the "solutions" you would like to follow - to see if anyone can think of any work arounds for not having ethernet.

---

### Post by shearn89 on 2007-06-28
If you go to google, and search for the package you have to find with "site:http://gb.archive.ubuntu.com/ubuntu/pool/" at the end, it should (hopefully) find the .deb file.

Assuming you need to download anything.

---

### Post by ubername on 2007-06-28
> **ugm6hr said:**
> Maybe post the output of *lspci* (in Terminal) - to inform us of your exact chipset (look for Ethernet / Network controller).

And post the links of the "solutions" you would like to follow - to see if anyone can think of any work arounds for not having ethernet.

lspci output looks like this (forgive typos, for obvious reasons I cant cut'n'paste)
01:00:0 Network controller: Boroadcom Corporation BCM4306 802.11b/g Wireless LAN controller (Rev 03)

[http://bcm43xx.berlios.de/](http://bcm43xx.berlios.de/) looks like somewhere to start but I guess it means compiling stuff which a) I haven't done before and b) might nee me to download stuff which takes me back to square one!

I do have a pen drive so can swap stuff downloaded from my connected PC to my old latop.

TIA

---

### Post by ugm6hr on 2007-06-29
This is probably what you want:
[http://ubuntuforums.org/showthread.php?t=201902&highlight=broadcom+43](http://ubuntuforums.org/showthread.php?t=201902&highlight=broadcom+43)

But there are lots of bcm 43xx how-to's on this forum (I don't have a Broadcom chipset).

If you are using Feisty - then I think Step 7 is the only one that will cause problems - try sheam89's suggestion re: packages ubuntu / google.

Maybe some of the other how-to's are more non-ethernet friendly?  Just look around.

---

### Post by ubername on 2007-07-06
Tara!

Done it!

It took quite a bit of work, not helped my me not understanding how to enter WEP codes etc. but eventually I got there.

Thanks for all the help.

---

### Post by ubername on 2007-07-06
I should acknowledge this in particular:

[http://ubuntuforums.org/showthread.php?t=201902&highlight=broadcom+43](http://ubuntuforums.org/showthread.php?t=201902&highlight=broadcom+43)

---

