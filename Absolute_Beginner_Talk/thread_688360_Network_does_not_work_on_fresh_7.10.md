---
title: "Network does not work on fresh 7.10"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by Yorii on 2008-02-05
I just installed Ubuntu on my computer, everything seems to work except my network.
The Motherboard is a ASUS P5LD2 SE, been searching on the forums but haven't found anyone with the same problem. (The NIC is a Realtek RTL8111B)
The device lists up properly, I can assign IP-addresses to it and can ping localhost, but that's how far it goes. It does not get a DHCP-address, but if I set a correct and working address and do a route add default gw with my routers IP-address it doesn't work.

I have downloaded proper drivers from Realteks webpage, but I have no idea how to install these ^^

Anyone have any idea what I should try to do?

---

### Post by Yorii on 2008-02-05
I managed to install the drivers, there was a readme ^^

But it's still the same problem as before, nothing has changed...

---

### Post by bumanie on 2008-02-05
You probably are suffering the ipv6 issue that has plagued some others using gutsy. You need to either alter settings in firefox or blacklist ipv6.
Method 1.
> gksudo gedit /etc/modprobe.d/blacklist
then add 
blacklist ipv6
at the bottom of the gedit list and save.
After reboot, all should work fine.
Method 2 (is to diable ipv6 in firefox)
Type about:config in your firefox address bar
Type "ipv6" in the filter 
Change the value of "network.dns.disableIPv6" to true
Hope this helps.

---

### Post by gupta_sumesh63 on 2008-02-05
Try and configure your network in system->administration->network, by adding your real IP address, DNS servers and gateway address. Then after saving reboot and configure your network tools(system-Administration->network tools.)
I hope it works after that.

---

### Post by hyper_ch on 2008-02-05
Are you sure you want DHCP? I prefer static IPs.

If you want a static ip you also need to set DNS servers in /etc/resolv.conf

---

### Post by Yorii on 2008-02-05
I've disabled ipv6, manually set IP, gateway and DNS and tried different cables. Still I can't even ping my own gateway. (which responds to ping perfectly on my laptop)

---

### Post by Yorii on 2008-02-05
I'm going to go through some old boxes and see if I can find another NIC.

---

### Post by Yorii on 2008-02-05
I found a wireless USB NIC that seems to work, I'll use this until I can figure the rest out ^^

---

