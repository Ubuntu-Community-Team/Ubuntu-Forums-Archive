---
title: "pppoe,dsl connection problems"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by phrgarek on 2007-09-14
Hi! 2 days ago, i installed Mint KDE 3.0 Cassandra.That distro is almost like ubuntu. Before MInt, i used opensuse for a long time... Mint looks really great for me, but till now, i can't
figured out 100% Mint's dsl connection tool pppoeconf...opensuse has great simple tool kinternet... and mint's is also pretty simple but i allways must configure my connection, i mean on every boot...i can connect,(running pppoeconf) but on new login connection resets...i red that many users had the same problem, i red many articles what must i do, but still can't manage that...i've installed rp-pppoe ,pppoe and pppd packages...here is my dsl-provider file from /etc/ppp/peers directory:
noipdefault
defaultroute
replacedefaultroute
hide-password
#lcp-echo-interval 30
#lcp-echo-failure 4
noauth
persist
#mtu 1492
#persist
#maxfail 0
#holdoff 20
plugin rp-pppoe.so eth0
usepeerdns
user "phrgarek@htnet-dsl"
-i don't know what else to do, if somebody knows right and specific solution, please help
THANKS

---

### Post by 22bsti on 2007-09-22
well, the easy way would be to handle the auth with a router or if your modem supports it in the modem, if you could provide some detailed info on your network setup, i may be able to help more

---

