---
title: "what happened to my network connection?"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by rickycodie on 2007-06-30
so i can't connect to the internet anymore, but i don't know why. how do i figure it out?

it was sorking fine at my dad's house and now it won't work at mine.

i have a toshiba laptop and my wife can use her internet, so it's not the router.

---

### Post by cmnorton on 2007-07-02
As a suggestion, I would search the Ubuntu forums for dhclient3. If your ethernet connection is dhcp, that is what starts your ethernet connection. I just checked ps -ef 

 ps -ef | grep dhclient3
dhcp      3536     1  0 07:19 ?        00:00:00 dhclient3 -pf /var/run/dhclient.eth0.pid -lf /var/lib/dhcp3/dhclient.eth0.leases eth0

and got this.

---

### Post by ev5unleash1 on 2007-07-02
Are you using Ubuntu 7.04? If you see your network but can't connect go to System > Administration > Network. Select the the Wireless connection and disable roming and type the wireless information in manually. Also make sure your wireless switch is switched on. Alot of notebooks have a feature. Also make sure your wireless is not a restricted driver if it is make sure it is enabled and working properly. Also if it is there is there is alot of problems that can happen to the connection so try alot of things. Like restarting, backing up data and reinstall ubuntu. Connect using a LAN cable and make sure you are up-to-date with ubuntu.

---

