---
title: "[SOLVED] HELP!!! Putty now NOT working!!!"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by BlizzofOZ on 2008-03-20
I had Putty working fine with local Ip address and also my new dns hostname.  I even had TightVNC connecting using local IP address.

I was having a problem getting my TightVNC over the internet and thought that the port I forwarded was maybe not setup in iptables.

So I went ahead and did this command:
iptables -I INPUT -p tcp --dport xxxxx -j ACCEPT

xxxxx = port I forwarded

After adding the port, I did iptables -L and saw the port listed

Since I did that, Putty has stopped connecting, giving me a time out on connecting.

I now cannot ping the server with its local IP.
I can still ping the dns hostname.

After rebooting, I did iptables -L and for some reason the port did now list.
Just for heck of it, I issued :iptables -I INPUT -p tcp --dport xxxxx -j DROP

After doing that, I still cannot connect.

Not sure what happened...  HELP!!!

My main concern is getting Putty and TightVNC to connect locally again... connecting via internet is a lower priority.

---

### Post by BlizzofOZ on 2008-03-21
Bump...

---

### Post by BlizzofOZ on 2008-03-21
Ok, I found the problem... my server's LAN IP address changed.

In my search to solve my remote desktop port forwarding problem, someone suggested in thread to restart the router... well, I believe that reset the IP addys.

I that normal?  Makes sense... to lost power, it can't maintain the addresses.

Need to keep that in mind the next time I loose power... :(

---

### Post by DezSP on 2008-03-21
By default, the router will assign IPs to all local machines mostly at random, if you need a PC to remain on a given IP, you should configure the machine to have it's own static IP address, Google's got some decent guides on how you can do this using iftables.

---

### Post by BlizzofOZ on 2008-03-21
> **DezSP said:**
> By default, the router will assign IPs to all local machines mostly at random, if you need a PC to remain on a given IP, you should configure the machine to have it's own static IP address, Google's got some decent guides on how you can do this using iftables.

You can configure the internal/LAN IP to be static?

---

### Post by mozetti on 2008-03-21
Yes. Using the networking tool (Administration) you can specify the IP to be static.

A couple caveats:

When running multiple PCs in a network, if one PC uses static IPs and the rest use DHCP then you need to make sure the static IP you give the PC isn't in the IP range of the DHCP server. For example, if you give the PC the IP 192.168.1.5 then you need to make sure the DHCP server only gives out IPs starting at 192.168.1.6 and higher. 2 PCs using the same IP on a network=trouble.  You should be able to set the DHCP server IP range in its configuration.

Depending on the router you have, you might be able to install 3rd-party firmware like DD-WRT, Tomato, OpenWRT, etc. Some of these have the option of statically assigning IP addresses from the DHCP server based on MAC address. This is what I've done using my Linksys WRT54G router running DD-WRT firmware. You give the router/DHCP server the MAC addresses of your network cards, tell it to assign 192.168.1.1 to MAC xx-xx-xx-xx-xx-xx, 192.168.1.2 to MAC xx-xx-xx-xx-xx-xx, 192.168.1.3 to MAC xx-xx-xx-xx-xx-xx, etc. In this setup, each PC is set up to use DHCP and the router works as the DHCP server but because you specifiied the IP addresses to give out based on the MAC, all the PCs will always have the same IP addresses.

---

### Post by BlizzofOZ on 2008-03-21
> **mozetti said:**
> Yes. Using the networking tool (Administration) you can specify the IP to be static.

A couple caveats:

When running multiple PCs in a network, if one PC uses static IPs and the rest use DHCP then you need to make sure the static IP you give the PC isn't in the IP range of the DHCP server. For example, if you give the PC the IP 192.168.1.5 then you need to make sure the DHCP server only gives out IPs starting at 192.168.1.6 and higher. 2 PCs using the same IP on a network=trouble.  You should be able to set the DHCP server IP range in its configuration.

Depending on the router you have, you might be able to install 3rd-party firmware like DD-WRT, Tomato, OpenWRT, etc. Some of these have the option of statically assigning IP addresses from the DHCP server based on MAC address. This is what I've done using my Linksys WRT54G router running DD-WRT firmware. You give the router/DHCP server the MAC addresses of your network cards, tell it to assign 192.168.1.1 to MAC xx-xx-xx-xx-xx-xx, 192.168.1.2 to MAC xx-xx-xx-xx-xx-xx, 192.168.1.3 to MAC xx-xx-xx-xx-xx-xx, etc. In this setup, each PC is set up to use DHCP and the router works as the DHCP server but because you specifiied the IP addresses to give out based on the MAC, all the PCs will always have the same IP addresses.


Funny, I just bought myself a WRT54GL wireless router... I know the most recent firmware.  How do you know if you have DD-WRT?

I have firmware v4.30.12... I see right in the main setup screen, under enable DHCP, setup for starting IP addy, max number of DCHP users and static DNSs... I don't see anyting for MAC address though.

---

### Post by mozetti on 2008-03-21
DD-WRT isn't from Linksys. It's a 3rd-Party firmware. Linksys used Linux as the firmware in the WRT54G series of routers. So, many different people/groups wrote their own replacement firmware. If you're up for getting into it, you can really add some nice features to these cheap routers. DD-WRT (and others) implement some features that are only available on higher-end/higher-priced routers.

Head on over to the [DD-WRT Wiki](http://www.dd-wrt.com/wiki/index.php/Main_Page) and get started. Check to make sure your router is [supported by DD-WRT](http://www.dd-wrt.com/wiki/index.php/Supported_Devices), first.

But, to answer your immediate question. Set your static IP address on the computer (say, 192.168.1.5 for example, but use whatever you want), then in the Linksys Firmware set the "Starting IP Address" to something higher than the static IP you just set. That way, any computers that get an IP address from the router won't get the same address you set as static on the computer.

---

### Post by supersonicdarky on 2008-03-21
The router doesn't come with dd-wrt, you have to install it your self.

[http://www.dd-wrt.com](http://www.dd-wrt.com)

Also, even if you have dhcp, you should be able to connect to the server by using it's hostname. I usually just **ssh server-01** when I need to ssh to it, although I have static ips for all machines in the house.

---

### Post by BlizzofOZ on 2008-03-21
> **supersonicdarky said:**
> The router doesn't come with dd-wrt, you have to install it your self.

[http://www.dd-wrt.com](http://www.dd-wrt.com)

Also, even if you have dhcp, you should be able to connect to the server by using it's hostname. I usually just **ssh server-01** when I need to ssh to it, although I have static ips for all machines in the house.

Oh, I didn't realize it was a 3rd party firmware...

---

### Post by BlizzofOZ on 2008-03-22
> **mozetti said:**
> Yes. Using the networking tool (Administration) you can specify the IP to be static.

A couple caveats:

When running multiple PCs in a network, if one PC uses static IPs and the rest use DHCP then you need to make sure the static IP you give the PC isn't in the IP range of the DHCP server. For example, if you give the PC the IP 192.168.1.5 then you need to make sure the DHCP server only gives out IPs starting at 192.168.1.6 and higher. 2 PCs using the same IP on a network=trouble.  You should be able to set the DHCP server IP range in its configuration.

Depending on the router you have, you might be able to install 3rd-party firmware like DD-WRT, Tomato, OpenWRT, etc. Some of these have the option of statically assigning IP addresses from the DHCP server based on MAC address. This is what I've done using my Linksys WRT54G router running DD-WRT firmware. You give the router/DHCP server the MAC addresses of your network cards, tell it to assign 192.168.1.1 to MAC xx-xx-xx-xx-xx-xx, 192.168.1.2 to MAC xx-xx-xx-xx-xx-xx, 192.168.1.3 to MAC xx-xx-xx-xx-xx-xx, etc. In this setup, each PC is set up to use DHCP and the router works as the DHCP server but because you specifiied the IP addresses to give out based on the MAC, all the PCs will always have the same IP addresses.

Yep, I moved the server into the cabinet which meant turning off the switch... reconnecting caused new IP address, which then caused Putty not to work.

So, taking your advice... I've reflashed my router's firmware to DD-WRT.  Resetup everything and I'm up and running... tried powering stuff down and back up with no change in IP addresses!

Thanks for your help!

PS:  If I've missed something, please let me know.

---

### Post by BlizzofOZ on 2008-03-24
> **mozetti said:**
> DD-WRT isn't from Linksys. It's a 3rd-Party firmware. Linksys used Linux as the firmware in the WRT54G series of routers. So, many different people/groups wrote their own replacement firmware. If you're up for getting into it, you can really add some nice features to these cheap routers. DD-WRT (and others) implement some features that are only available on higher-end/higher-priced routers.

Head on over to the [DD-WRT Wiki](http://www.dd-wrt.com/wiki/index.php/Main_Page) and get started. Check to make sure your router is [supported by DD-WRT](http://www.dd-wrt.com/wiki/index.php/Supported_Devices), first.

But, to answer your immediate question. Set your static IP address on the computer (say, 192.168.1.5 for example, but use whatever you want), then in the Linksys Firmware set the "Starting IP Address" to something higher than the static IP you just set. That way, any computers that get an IP address from the router won't get the same address you set as static on the computer.

I was curious if on your WRT54G, do you have to run ddclient or something similar?  Again, I have wireless WRT54GL... I'm under the impression that I may need to run ddclient to update the new IP address.

Not sure if I need to do that with my router...

---

### Post by mozetti on 2008-04-02
Sorry, just got back to this.

Yes, DD-WRT supports running a ddclient. It actually supports more dynamic DNS services than the original linksys firmware does. I forget exactly where it is, but I just set it up last week to use no-ip.com dynamic DNS service.

Check the DD-WRT wiki or forums and you should be able to find the menu that has that option.

---

### Post by BlizzofOZ on 2008-04-02
> **mozetti said:**
> Sorry, just got back to this.

Yes, DD-WRT supports running a ddclient. It actually supports more dynamic DNS services than the original linksys firmware does. I forget exactly where it is, but I just set it up last week to use no-ip.com dynamic DNS service.

Check the DD-WRT wiki or forums and you should be able to find the menu that has that option.

Thanks... I'm all setup now.

I think I'll mark this a solved...

---

