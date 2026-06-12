---
title: "Lost wicd AND Network manager! No connection now!"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by TriadDraykin on 2008-03-04
Well, ya'll can call me the biggest idjit you've ever seen if ya want, and I'd agree with ya. I've managed to entirely disable Ubuntu's ability to connect wirelessly by switching to Wicd, in the process uninstalling Network manager, deciding i didn't want to bother with it, and then uninstalling wicd.

Yes, go ahead and laugh if you've realized what I've done: I've taken away both of the programs that connect Ubuntu, and its subsequent Add/Remove programs, to the Internet that they both function on. I can no longer re-install Network Manager via A/R P, since their source is online. 

Any attempt to find an offline version of this to install locally has led to confusion, and so I turn to the Ubuntu community and request assistance. 

Please?

-Triad Draykin

---

### Post by Whiffle on 2008-03-04
lol.  I've done worse. :)


Are you on an open wireless network?  If so, you can open up a terminal and run:
```

sudo iwconfig <your interface> essid <your wireless network>

```
and then
```

sudo dhclient <your interface>

```

and it should get you back online.  

If you're not on an open wireless, we'll have to get into wpa_supplicant.

---

### Post by TriadDraykin on 2008-03-08
```

triad@triad-laptop:~$ sudo iwconfig ath0 essid logan
triad@triad-laptop:~$ sudo dhclient ath0
There is already a pid file /var/run/dhclient.pid with pid 17765
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/


wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:11:f5:c5:d1:cb
Sending on   LPF/ath0/00:11:f5:c5:d1:cb
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 16
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

That's from a local network that's not very local... From what I can gather, it didn't get a response, which doesn't surprise me, as I usualy can't connect to it. The reason i did, is that it's unsecured.

The network I DO connect to normally, is encrpyted. WEP, if i remember right, and there's no way in hell they'll (landlords)  let me unsecure it for even a a second. In their minds, everyone in a 4-block radius is constantly trying to attack their computers by their signal.

---

### Post by Whiffle on 2008-03-08
Just for kicks, what happens if you try to install wicd or network manager?  Assuming you didn't delete them and you had downloaded them already, they might be cached.  If not, then you can do WEP with wpa_supplicant.

---

### Post by mikespug on 2008-03-12
Check in /var/cache/apt/archives for "leftover" packages from both wicd and network manager.  You should be able to reinstall either using these.  Look for network-manager* (there are two packages, or wicd*, depending on which you would like to reinstall.

---

