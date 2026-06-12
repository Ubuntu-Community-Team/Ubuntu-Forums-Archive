---
title: "Not detecting my ethernet card!!??!!"
date: 2006-03-09
forum: Absolute Beginner Talk
---

### Post by AlaskaLinux on 2006-03-09
I have been digging through the forums but cant seem to find out how I go about getting ubuntu to see my ethernet... it doesnt even list an "eth0". I have a wireless and a hardwire card, both pci, both not being seen!!! I LOVE Ubuntu and want to keep using it, being MS free has always been a dream and im not completely retarded so I think I can handle it. Some friendly advise would be appriciated.. I dont wanna go back to XP!!!!!!

Thanks!
Nick

---

### Post by kaamos on 2006-03-09
If you open a terminal (Applications->Accessories->Terminal) and type
```
lspci
```
do either of the cards show up?

For example, my output is
[...]
0000:02:0c.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
0000:03:00.0 Ethernet controller: Linksys, A Division of Cisco Systems [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)

---

### Post by AlaskaLinux on 2006-03-09
Thanks for the fast reply!!! Yes, one of them shows up "Ethernet controller: Marvell Technology Group Ltd.: Unknown Device lfaa (rev 03)". That is it though, the other one is not showing. Im not sure if the "Marvell Technology" one is my wireless or my hardwire, I need to setup my hardwire. Please!! More help!! LOL

Nick

---

