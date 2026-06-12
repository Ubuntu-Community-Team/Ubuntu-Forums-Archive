---
title: "fixed channel -1 on mon0 (b43)"
date: 2012-01-27
forum: Any Other OS
---

### Post by shot00 on 2012-01-27
Hi,
recently install linux mint 12 and decide to work with aircrack.
But  some problems occured while doing
sudo airodump-ng -c 6 --bssid (mac ad) -w psk mon0
i get on top right corner an error that says fixed channel -1.

While i tried to do deauth:
sudo aireplay-ng -0 1 -a (mac bssid) -c (clients mac) mon0
i get
Waiting for beacon frame (BSSID: 00:05:59:0C:49:78) on channel -1
 mon0 is on channel -1, but the AP uses channel 6

So, what's the problem here?
I'm using b43 driver
If anyone knows i'll appreciate it

---

### Post by shot00 on 2012-01-27
Allright,
I managed to solve the fixed channel problem by installing compat wireless 
but after a restart i had no wireless connection.
iwconfig didn't show any drivers too.
I did modprobe b43 but said invalid argument....

Please someone help here!

---

### Post by howefield on 2012-01-27
Thread moved to the "*Other OS/Distro Talk*" forum.

---

