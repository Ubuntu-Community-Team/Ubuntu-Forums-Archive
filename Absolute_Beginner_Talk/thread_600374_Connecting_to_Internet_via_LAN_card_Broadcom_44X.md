---
title: "Connecting to Internet via LAN card Broadcom 44X"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by psanu on 2007-11-02
Hi,

I am new to UBUNTU (duh !!) and i have been working with a vista Fiesty dual boot system. Dell 6400 2 GB ram. Earlier i used to connect to Net via ADSL which i managed to configure for both OS. Now i have shifted place and only ISP at my new place is providing cable via CAT5 cable which goes to my LAN card. 

In vista the connection is easy and i could connect to Net without any dialer . The ISP does provide Dialer for Redhat and Fedora Core(and XP too, Vista does not need a dialer) . But they do not support Ubuntu at the moment. I am at a loss to proceed. Any hints in any directions will help a lot.

Thanks.

Psanu

Dell 6400
2gb Ram , 160 Gb HDD
Vista / Fiesty Dual boot

---

### Post by damotor on 2007-11-02
If you get internet through rj45 cat 5 ethernet cable I don't think you need extra configuration, try the livecd and if you get internet with that you will only need to plug the cable and dhclient the interface. If the modem or router that is connected to your computer does not support dhcp you will have to configure ubuntu with an ip, network mask, etc It should be in the documentation from your ISP.

---

### Post by psanu on 2007-11-02
Thanks for such a quick reply. 

I guess this should be easier but being a life long Windows user i find it a bit difficult.

> 
If you get internet through rj45 cat 5 ethernet cable I don't think you need extra configuration, try the livecd and if you get internet with that you will only need to plug the cable and dhclient the interface

I have no idea what dhclient is. Any specific place i should look into regarding this?

Thanks

Psanu

---

