---
title: "Problem with Wlan and Xubuntu"
date: 2006-11-26
forum: Absolute Beginner Talk
---

### Post by kavelman on 2006-11-26
Hi there,

i've got a problem with my acer aspire 5022 WLMI notebook and my Wlan connection.
For some reason Xubuntu won't let me access my access point but that's because the Wlan-card isn't installed properly yet.
At first I tried to configure my Wlan-card with the network-config tool From Xubuntu and it seemed as if it worked correctly...but somehow...I had no connection to my access point...
Then I found out with ifconfig and iwconfig that there isnt any connection named wlan0 or something like that...but there was a connection named eth1 which is actually my broadcom BCM4318 Wlan-card...but as I already said, it doesn't work!
Then I used my good old friend google to find some help and there i found that i had to install ndiswrapper and load a WinXp driver for my Wlan-card, but although I didn't have any errors it still wouldn't work.

And now I hav absolutely no clue what to do, can anyone help me with this problem, because I'm quite new to Xubuntu and Linux (installed it 3 days ago)
I would really appreciate any help of you guys,
thank you a lot!

---

### Post by justifier on 2006-11-26
it could be ra0 i know my wireless card is, make sure you have all the correct drivers installed, is the network encrypted? wep? wpa?

---

### Post by kavelman on 2006-11-28
Hi,

no unfortunately it's no ra0 it is actually eth1 (eth0 is my lan-card) but xubuntu won't let me activate this adapter.
if I use ifconfig eth1 up then it tells me "SIOCSIFFLAGS : No such file or directory"

what does that mean?

---

