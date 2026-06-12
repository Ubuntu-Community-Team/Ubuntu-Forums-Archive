---
title: "Internet Connection Issue in Gutsy.."
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by jeric2k5 on 2008-03-07
Ok so I previously had Gutsy installed on my HP dv9500t (with Santa Rosa chipset) and I easily had the internet working before. But I repartitioned my hard drive so I lost the Ubuntu partition and I had to reinstall it. After reinstalling it though I noticed I couldn't connect to the internet. Its the funniest thing though because when I enter my interformation into the network manager it connects to my network, but when I go on Firefox or try to use any internet features it simply doesn't connect.

I checked and it recongizes my WiFi card, but maybe I need to upgrade the firmware or something? Any help would be great and its an Intel card thats in the Santa Rosa - Centrio Pro - chipset. Any help would be great guys. Thanks!

---

### Post by lswest on 2008-03-07
after you connect to your wireless can you post the output of:
```
iwconfig
ifconfig
sudo dhclient [device name (eth1 or wlan0 depending on the card)]
```

---

