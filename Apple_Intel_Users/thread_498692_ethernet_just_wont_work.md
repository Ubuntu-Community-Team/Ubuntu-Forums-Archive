---
title: "ethernet just wont work"
date: 2007-07-11
forum: Apple Intel Users
---

### Post by ultihero on 2007-07-11
ok so i finally got to install ubuntu on my friends laptop. i got all the partitioning right and got it installed. the only problem is that the wireless does not innatly work so i have to install those drivers for it im sure. unfortuanetly my ethernet wont work at all either. the network manager will say it is connected. but nothing i connect to will work. i tried different cords on the mac, and i tried it it on all different comps and they work as well. of course im writing this on another comp cause i dont have any way of internet on this mac. my router is 192.168.1.1 with a subnet of 255.255.255.0 i pinged it and it recieved data from it still. when i got to ifconfig it tells me that the eth0 is
HWaddr 00:1B63:1C:16:E9
 inet of 192.168.1.104
Bcast of 192.168.1.255
Mask 255.255.255.0

ive tried restarting, and it still works perfectly in OSX as well.
please help thank you

---

### Post by benanzo on 2007-07-11
It looks like you're getting an IP address from your router, so the connection isn't the problem.  What exactly wont work?  Is it that you can't connect to any websites or dowload updates?  If that is the case you could be having trouble with the DNS server that your ISP uses. Try using a DNS service like OpenDNS.

Go to **System -> Administration -> Network**  Then select the **DNS** tab and delete the entries (if any) in the **DNS Servers** box and add: **208.67.222.222** and **208.67.220.220**.  Delete the entry (if any) in the **Search Domain** box.  Then try to connect to a website.

---

### Post by ultihero on 2007-07-11
yeah, i cant connect to any website, in firefox it automatically brings me to a server not found page, and gaim never connects either. i tried what you said, and yeah i had a .comcast in the search domains box or something like that. and i put those two new ones in, but it still brings me directly to a server not found

---

### Post by ultihero on 2007-07-11
ok update, so i booted from my live cd that i installed ubuntu with and the internet works perfectly on it

---

