---
title: "How tell if you have a Static IP address"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by BlizzofOZ on 2008-03-20
Everytime I reboot and visit portforwarding.com, the same IP address comes up... 

Does this mean my IP do not change and that it is static?

---

### Post by aashay on 2008-03-20
The site you mentioned failed to load. if it is anything like [http://www.whatismyip.com/](http://www.whatismyip.com/) Yes, if the ip shown is same each time, it is static as far as the internet is concerned. You might also want to run ifconfig to check the local address

---

### Post by (((X))) on 2008-03-20
No, it not always mean it is static

---

### Post by jseiser on 2008-03-20
I work at an ISP in Ohio, so this might be different for you.  We do not give out static IP's unless a customer requests it, and we charge an extra 5 dollars a month for that.  So chances are, if you didnt ask for one, you dont have one.  Normally the IP's are served dynamicly, then you stick a router behind your modem, set up your forwarding on that, and assign each computer an IP conforming to your network.  That is how i handle my forwarding for torrents etc.  This is off your question, but if you are dealing with port forwarding, im guessing your behind a router.  Just set up a static IP on the machine, and then log into your router, and enter in that IP, and what you want forwarded etc. Make sure the static IP you are giving yourself is outside the range od the DHCP if you still have it enabled for other PC's.


edit: you are probably seeing the same IP, because your modem has that IP address, and you are just rebooting your PC, which has a dynamic LOCAL address.  Power cycle your equipment, and I imagine you will see a different IP. you could always plug the PC right into the modem, do a ifconfig, the default gateway is the modems IP.  go to port forwarding, thats the IP you will see.  power cycle, do a ifconfig, the default gateway has probably changed, because the modem now has a new IP, check on that site, and you will now see that new IP.

---

### Post by p221072 on 2008-03-20
Even if your IP is not static sometimes the DHCP keeps IP addresses associated to a MAC address for certain time before giving the same IP to someone else. According to its settings it could keep on giving you the same IP even if you are offline for a day or more, but this doesn't mean your IP add is static.

---

### Post by BlizzofOZ on 2008-03-20
> **aashay said:**
> The site you mentioned failed to load. if it is anything like [http://www.whatismyip.com/](http://www.whatismyip.com/) Yes, if the ip shown is same each time, it is static as far as the internet is concerned. You might also want to run ifconfig to check the local address

Sorry, site is portforward.com... been posted many times on this forum.

---

### Post by BlizzofOZ on 2008-03-21
> **jseiser said:**
> 
edit: you are probably seeing the same IP, because your modem has that IP address, and you are just rebooting your PC, which has a dynamic LOCAL address.  Power cycle your equipment, and I imagine you will see a different IP. you could always plug the PC right into the modem, do a ifconfig, the default gateway is the modems IP.  go to port forwarding, thats the IP you will see.  power cycle, do a ifconfig, the default gateway has probably changed, because the modem now has a new IP, check on that site, and you will now see that new IP.

I've rebooted, powered down equipment and had even added a switch... when I go to Portforward.com to check my external IP, comes up with the same address.  This is the 3rd day and still the same address.

Doesn't matter as I've already went the dyndns.com and created a dns hostname...

---

### Post by Junglizer on 2008-03-21
Usually  you will have to pay more from your ISP for a static, and based on the ISP usually there is some clause for leasing a new IP. In most cases simply power-cycling the devices will not change the IP as most dhcp leases from ISP's are in the day range. If you leave your modem off for 24hrs or longer you can almost guarentee you will get a new IP when you turn it back on. Also this can be seen with medium to large area power outages.

---

