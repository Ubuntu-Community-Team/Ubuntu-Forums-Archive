---
title: "Upgraded"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by rbhigday on 2007-06-24
I upgraded my Dell Latitude 600 to 7.04 a few days ago. every thing seem ok with one little exception.
No wireless, where do I start to reinstall this I seem to lost the link for the wireless guide.

---

### Post by Pragmatist on 2007-06-24
[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

---

### Post by rbhigday on 2007-06-27
Thanks for the help it appears my Netgear WG111 is not supported for my Latitude c600. Does anyone know of a network card that will work with Feisty fawn and my system or must I downgrade back to edgy?

---

### Post by DSn0wMan on 2007-06-27
If your card was supported under edgy, it should still be supported  with Feisty. The thing that messed me up with feisty is the ease with witch you can get your wireless working (Dell Inspiron 6000 w/ centrino). All I had to do was click on the network icon select my wireless network, and enter my WPA passphrase.

---

### Post by rbhigday on 2007-06-30
Unfortunately during the upgrade my wireless network connection was removed.

Also not my light on my usb WG111 no longer comes on. I have plugged in the wg111 to windows and it see it and recognized new hardware, so I know it still working. I am wondering what version it is since I have forgot, will have to determine what it is again and figure out how to install software that will detect that it is connected at least.

edited, added below

lsusb list nothing

on edgy i had

Bus 00x Device 00x: ID 0846:4240 NetGear, Inc. WG111 WiFi (v2)

which is version 1 of WG111, yes it is labeled wrong.

iwconfig

lo       No wireless extensions.
eth0  no wireless extensions.

When i try to follow the old version to install the software I get NDISwrapper 1.8 is missing, what is the next version or program to replace this? guess i go searching again :)

Ndiswrapper went down to 1.47 from 1.8?!?!?! did I dl the wrong one?

This version does not want to install

---

### Post by louieb on 2007-06-30
check to see if  network-manager or wifi-radar is installed . also look and see what restricted modules are installed.

---

### Post by jimrz on 2007-06-30
> **rbhigday said:**
> Thanks for the help it appears my Netgear WG111 is not supported for my Latitude c600. Does anyone know of a network card that will work with Feisty fawn and my system or must I downgrade back to edgy?

netgear wg511t...has atheros5212 chipset and works OTB with feisty, as it did on previous versions at least back to breezy...uses the madwifi driver and is automatically detected at install

---

### Post by rbhigday on 2007-07-01
> **jimrz said:**
> netgear wg511t...has atheros5212 chipset and works OTB with feisty, as it did on previous versions at least back to breezy...uses the madwifi driver and is automatically detected at install

Does it work on a dell Latitude C600?

---

### Post by Pragmatist on 2007-07-01
> **rbhigday said:**
> Does it work on a dell Latitude C600?

It looks like it is just a PCMCIA card.  Do you have a PCMCIA slot?

---

### Post by rbhigday on 2007-07-01
> **louieb said:**
> check to see if  network-manager or wifi-radar is installed . also look and see what restricted modules are installed.

Network-Manger is loaded and no restricted modules.

It does not list a wireless connection just the wired and the loop

----------------------------------

Side note I wiped the drive and reinstalled 7.04 from the CDrom since the upgrade appeared to be buggy and have problems. So now I can hopefully solve this sooner :)



lsusb list nothing


iwconfig

lo No wireless extensions.
eth0 no wireless extensions.

---

### Post by rbhigday on 2007-07-01
just bought the card mentioned above. since my usb modem has to many problems nice to have one work otb

---

### Post by jimrz on 2007-07-01
> **rbhigday said:**
> Does it work on a dell Latitude C600?

it is a pcmia card that works quite well with feisty, so if you have a pcmia slot it will do just fine

---

### Post by rbhigday on 2007-07-05
Well the new card came and after a bit of tinkering I am now posting this message from my laptop :) thanks for the help the new wireless net card was worth every bit of the 21 bucks it cost :)

---

