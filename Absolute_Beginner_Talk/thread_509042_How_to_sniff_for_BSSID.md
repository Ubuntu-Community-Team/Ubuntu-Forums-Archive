---
title: "How to sniff for BSSID?"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by TarB on 2007-07-24
My wireless adapter detects many access points, all of them are WEP encrypted. I was wondering, what is the code to sniff for the BSSID of those access point (MAC addresses), using Aircrack-ng or some other utility?

---

### Post by moffa on 2007-07-24
Yes, you can use aircrack-ng.  You have to set you adapter to monitor mode (which may require you to rebuild and patch your kernel) and then use airdump-ng i think.  Aircrack's website has a good tutorial.

---

### Post by TarB on 2007-07-25
I understand that I need to use that utility, but what is the command that I need to put ?

---

### Post by moffa on 2007-08-07
sudo airmon-ng start eth1 6

to use eth1 to monitor channel 6 (the channel is optional)

then sudo airodump-ng eth1

and it'll start to collect packets and you'll find the bssid after some time

---

