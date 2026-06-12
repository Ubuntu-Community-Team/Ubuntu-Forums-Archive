---
title: "Network config issues"
date: 2007-07-18
forum: Apple PPC Users
---

### Post by ajmctaggart on 2007-07-18
EDIT:  GOT EVERYTHING WORKING, BUT WHY DOESN'T NETWORK MANAGER WORK LIKE IT USED TO?  IT WON'T SHOW ME AVAILABLE WIRELESS ANYMORE, ANYONE GOT ANY IDEAS, JUST SHOWS ME CONNECTED TO ETH0...


Hey everyone,

I have a Powerbook Pismo w/ a Buffalo wireless card, I have tried a number of things to get it to work, and that indeed may be my problem!  But here goes,

My /etc/network/interfaces files is completely trashed, I have the auto lo loopback, and my hard ethernet connection (eth2).  First off, what happened to eth0 and eth1?  My card is being recognized under iwconfig as eth3, but no eth3 in /etc/network/interfaces.

Is there anyway to do a reconfiguration of my /etc/network/interfaces file?  I feel this would be best...
If anyone has a good configuration, please feel free to post it!

Thanks,
ajm

---

### Post by Tommy on 2007-07-19
Network Manager has gone through a lot of changes since Dapper 6.06. You don't say which version Ubuntu you have installed, and whether you upgraded or installed "clean."

If you can, I would recommend installing from "scratch" -- the newer network manager versions "auto configure" your settings, so you don't NEED your networks defined in the same way as before. (On an upgrade I think it will use your old configuration if present, which may have caused the confusion.)

If you feel you cannot upgrade OR you just want to learn more about the network configuration, you might dig around the FAQs and/or check the more general forums. Fortunately these issues are NOT PowerPC specific, so lots of folks can help.

---

