---
title: "airodump-ng isn't capturing handshakes"
date: 2016-08-05
forum: Any Other OS
---

### Post by linuxnoob4 on 2016-08-05
Specs:
Architecture-Kali 64-bit (live CD & Vitrual Box version)
Wi-Fi Adapter- USB ALFA Network 802.11b/g/n Long_Range USB Adapter (tinyurl snipped)

Problem: So to start I run airmon-ng check and kill the processes, then I start monitor mode and get wlan1mon, run airodump-ng wlan1mon, and get my wi-fi's MAC address, but after running the second airodump-ng scan it wont collect any handshakes. I use aireplay-ng to send a deauth and my phone disconnects from the wi-fi and it reconnects. I let this run for a few hours and still no handshakes. My wi-fi adapter is supported and I cant find any solutions online. I have tried in virtual box, and live CD/USB and always get the same problem. I have run distro update and apt-get update/upgrade and let the crap update. I don't know what else to do. One time I even sat right next to my router and still no handshakes. I am still getting beacons and data but no handshakes.

---

### Post by QIII on 2016-08-05
Hello!

Although we have no particular reason to believe you have any but the most honorable intentions, we do not allow discussions of this nature on the Ubuntu Forums.  They have the potential to drift into support for illegal activities and to provide a resource for those with nefarious intent.

Please refer to the [Ubuntu Forum Rules]("https://ubuntuforums.org/misc.php?do=showrules"), in particular:

> Cracking: Requests for help about any form of password or encryption "cracking" are not supported. Even though there are packages such as aircrack in the repositories, discussions about cracking or software related to cracking often lead to discussions about illegal activities. Such threads will be closed.

This may be the sort of thing you can ask on the [Kali forums]("https://forums.kali.org/").

---

