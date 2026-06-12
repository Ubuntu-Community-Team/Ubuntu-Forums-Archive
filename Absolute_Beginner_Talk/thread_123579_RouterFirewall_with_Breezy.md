---
title: "Router/Firewall with Breezy"
date: 2006-01-30
forum: Absolute Beginner Talk
---

### Post by Invicta on 2006-01-30
Greetings. 

I'm trying to share my internet connection with a linux box, and I thought to try Breezy + Firestarter -combination.

I have 3 NICs in the linux box, eth0 is external network, and eth1 and eth2 go to my other two pc's running WinXP.

My internet connection goes through my university LAN, and my support there says that absolutely no DHCP-transmissions are allowed towards the university network.

How do I set up this system, so that the linux box gets configured from the university network via DHCP, and my other computers share the internet connection, but do not use DHCP? Static IPs?

I'm not very familiar with linux in general, so easy-to-follow instructions would be great. :)

My greatest thanks!

--Invicta

---

### Post by mips on 2006-01-30
Just set eth0 up for static and the rest for DHCP. Seeing the network is so small i would just use static for all interfaces.

[http://www.ubuntuforums.org/showthread.php?t=111972](http://www.ubuntuforums.org/showthread.php?t=111972)

---

### Post by Invicta on 2006-01-31
That's a great guide, thanks for the link. 
Is it certain no DHCP data goes out with this method? I ask because the university network admins threaten to cut off the internet connection if this happens.. :)

Thank you very much!

--Invicta

---

### Post by mips on 2006-01-31
> Is it certain no DHCP data goes out with this method? I ask because the university network admins threaten to cut off the internet connection if this happens..

DHCP & BOOTP requests use broadcasts to work, IP Address 255.255.255.255 UDP Ports 67&68.

By default a router does not forward broadcast traffic unless specifically configured to do so. But I'm not 100% certain about linux but it should not.

You can check your IPTables for something like:
```
# iptables -t nat -A PREROUTING -p udp --dport 67......
```

If you want to make really certain you can configure you pc to drop traffic originating & incoming on eth1&2 using address 255.255.255.255 UDP ports 67/68.

If you are anal about security I would block all tcp/ip ports and only allow those that are required.

[http://lartc.org/howto/](http://lartc.org/howto/)

---

