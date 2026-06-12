---
title: "plzz help me"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by coolnik6 on 2008-02-22
i have dual boot 
ubuntu 7.10 n win xp
in xp my adsl router is configured in birdge mode n each time i login in windows i have to dial up a connection
in ubuntu when i try  command
sudo pppoeconf 
it says canot find  pppoe access concentrator
im trying this for last 3 months hoping it will work some day
but still no results
plzz help me
also plzz suggest me  to configure my router in another mode if it can solove my problem
also i cannot view my router's configuration page in ubuntu

---

### Post by superprash2003 on 2008-02-22
what you could do is,..login to windows xp.. and change your modem settings from bridge mode to ppoe mode.. then your modem will do the dialing.. so you dont need a dialer for your computer.. and make sure dhcp is turned on in your modem(it usually is..just verify)...
  in ubuntu go to system->administration->network tools and set your ethernet adapter(eth0 or eth1 depends on ur pc).. to DHCP!!

---

