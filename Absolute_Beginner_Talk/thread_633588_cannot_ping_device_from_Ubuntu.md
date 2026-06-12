---
title: "cannot ping device from Ubuntu"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by port23user on 2007-12-06
I have a networking issue that I can't figure out.  Here are my devices:

Laptop (wifi)
Windows XP
192.1.1.30 (dhcp)

Desktop (ethernet)
Ubuntu 7.10
192.1.1.120

Router
Linksys WRK54G
192.1.1.1
mask 255.255.255.0

I have AP isolation off and no firewalls.  From my laptop, I can ping the desktop's IP address fine.  From my desktop, I can't ping my laptop but I can ping the router.  Is this a router configuration issue?  What do I need to do to fix it?  Thanks!

---

### Post by PeterJS on 2007-12-06
Do you have a firewall on the laptop? Most firewall will drop pings by default.

---

### Post by port23user on 2007-12-07
Nope, none at all.  I checked the Windows security center to be sure and the firewall is, in fact, off.

---

### Post by CaptainInsaneO on 2007-12-07
This will sound like a dumb question, but it's still viable:

Did you configure your router over an ethernet connection? There's a known issue with Linksys wireless routers where people take over and configure OTHER people's routers without even realizing it because they configured it over the wireless connection.

When you ping your desktop, you may actually be pinging someone else's machine on their router, this could also account for not being able to reach your desktop. If you are able to ping one way, you should definitely be able to ping the other way.

[http://www.shandyking.com/2007/02/18/hijack-hacked-linksys-wireless-router/](http://www.shandyking.com/2007/02/18/hijack-hacked-linksys-wireless-router/)
Here's a blog about it in case you're interested.

---

### Post by port23user on 2007-12-07
Thanks for the link.  I did configure the router over ethernet, so that's out of the question.

I logged into the router and did a ping test to my desktop and to my laptop.  Every time I ping the desktop, it shows a ping time of 0 ms.  However, when I ping my laptop, about 30% of the pings result in 16ms.  Should this be expected?

---

### Post by port23user on 2007-12-07
I did some more testing on it.  Here is what I found:
When I do an arp, the IP address of the laptop is found, but under HWaddress, it says "(incomplete)".

So I thought maybe there's a problem with my laptop responding to arp requests.  I loaded up Wireshark and captured the traffic on the network.  When I would try to ping, nothing came back.

So I ended up changing the IP address from DHCP on my laptop to a static.  Now it works.  Is there a way I can change my laptop back to DHCP and have it work?  Would this be a Linksys issue?

---

### Post by CaptainInsaneO on 2007-12-07
Try adding your laptop's MAC address to your ARP table manually. That might help, but I'm not sure. It's worth a shot.

---

### Post by port23user on 2007-12-08
So I ended up just setting my laptop's IP address to static and it works now.  Seems odd though that it didn't work when it got the address via dhcp.  Not sure what I'll do when if I have devices that require addresses via dhcp...

---

